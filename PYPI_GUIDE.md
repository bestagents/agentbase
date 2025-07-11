# PyPI Upload Guide for AgentBase

This guide explains how to upload the AgentBase package to PyPI.

## Prerequisites

1. **Create PyPI Account**: Register at https://pypi.org/account/register/
2. **Create TestPyPI Account**: Register at https://test.pypi.org/account/register/
3. **Install Twine**: `pip install twine`
4. **Generate API Token**: Go to PyPI Account Settings > API tokens > Add API token

## Step 1: Build the Package

```bash
# Clean previous builds
rm -rf dist/ build/ *.egg-info/

# Build the package
python -m build
```

This will create:
- `dist/agentbase-0.1.0.tar.gz` (source distribution)
- `dist/agentbase-0.1.0-py3-none-any.whl` (wheel distribution)

## Step 2: Upload to TestPyPI (Recommended First)

```bash
# Upload to TestPyPI first to test
twine upload --repository testpypi dist/*
```

You'll be prompted for:
- Username: `__token__`
- Password: Your TestPyPI API token

## Step 3: Test Installation from TestPyPI

```bash
# Install from TestPyPI to test
pip install --index-url https://test.pypi.org/simple/ agentbase
```

## Step 4: Upload to PyPI

Once everything looks good on TestPyPI:

```bash
# Upload to PyPI
twine upload dist/*
```

You'll be prompted for:
- Username: `__token__`
- Password: Your PyPI API token

## Step 5: Verify Installation

```bash
# Install from PyPI
pip install agentbase

# Test the installation
python -c "import agentbase; print('AgentBase v' + agentbase.__version__ + ' installed successfully!')"
```

## Configuration Files

### `.pypirc` (Optional)

Create `~/.pypirc` to avoid entering credentials each time:

```ini
[distutils]
index-servers =
    pypi
    testpypi

[pypi]
username = __token__
password = your-pypi-api-token

[testpypi]
repository = https://test.pypi.org/legacy/
username = __token__
password = your-testpypi-api-token
```

## Version Updates

To release a new version:

1. Update version in `agentbase/__init__.py`
2. Update version in `pyproject.toml` (if using)
3. Update `CHANGELOG.md` with new changes
4. Build and upload:
   ```bash
   python -m build
   twine upload dist/*
   ```

## Security Best Practices

1. **Use API Tokens**: Never use passwords, always use API tokens
2. **Scope Tokens**: Create project-specific tokens with minimal permissions
3. **Environment Variables**: Store tokens in environment variables:
   ```bash
   export TWINE_USERNAME=__token__
   export TWINE_PASSWORD=your-api-token
   ```
4. **CI/CD**: Use secrets management for automated uploads

## Troubleshooting

### Common Issues:

1. **File already exists**: You cannot upload the same version twice
   - Solution: Increment version number

2. **Invalid credentials**: Check your API token
   - Solution: Regenerate token and update configuration

3. **Package name conflict**: Name might be taken
   - Solution: Choose a different package name

4. **Missing files**: Check MANIFEST.in
   - Solution: Ensure all required files are included

### Validation

Before uploading, validate your package:

```bash
# Check package metadata
twine check dist/*

# Validate README rendering
python -m readme_renderer README.md
```

## Post-Upload

After successful upload:

1. Check your package page: https://pypi.org/project/agentbase/
2. Verify installation: `pip install agentbase`
3. Update documentation with installation instructions
4. Create a GitHub release
5. Announce on social media/communities

## Automation

Consider setting up GitHub Actions for automated PyPI uploads:

```yaml
# .github/workflows/publish.yml
name: Publish to PyPI

on:
  release:
    types: [published]

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.8'
      - name: Install dependencies
        run: |
          pip install build twine
      - name: Build package
        run: python -m build
      - name: Publish to PyPI
        env:
          TWINE_USERNAME: __token__
          TWINE_PASSWORD: ${{ secrets.PYPI_API_TOKEN }}
        run: twine upload dist/*
```

---

**Note**: Always test on TestPyPI before uploading to PyPI, as PyPI uploads are permanent and cannot be easily undone. 