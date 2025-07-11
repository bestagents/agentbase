# AgentBase Landing Page

A modern, responsive landing page for the AgentBase project - an open source storage solution for AI agents.

## 🚀 Live Demo

This landing page is designed to be deployed on GitHub Pages. Once deployed, it will be available at:
`https://omniagents.github.io/agentbase/`

## 📁 Files

- `docs/index.html` - The main landing page with embedded CSS and JavaScript
- `README.md` - This file with deployment instructions

## 🛠️ Features

- **Responsive Design**: Works perfectly on desktop, tablet, and mobile devices
- **Modern UI**: Clean, professional design with smooth animations
- **Interactive Elements**: Copy-to-clipboard functionality, smooth scrolling, hover effects
- **SEO Optimized**: Proper meta tags and semantic HTML structure
- **Performance**: Optimized for fast loading with inline CSS/JS
- **Accessibility**: Proper contrast ratios and semantic markup

## 🚀 Deployment to GitHub Pages

### Method 1: Using GitHub Pages Settings (Recommended)

1. **Push to your repository**:
   ```bash
   git add .
   git commit -m "Add landing page for AgentBase"
   git push origin main
   ```

2. **Enable GitHub Pages**:
   - Go to your repository on GitHub: `https://github.com/omniagents/agentbase`
   - Click on "Settings" tab
   - Scroll down to "Pages" section
   - Under "Source", select "Deploy from a branch"
   - Select "main" branch and "/docs" folder
   - Click "Save"

3. **Access your site**:
   - GitHub will provide you with a URL like: `https://omniagents.github.io/agentbase/`
   - It may take a few minutes for the site to be available

### Method 2: Using GitHub Actions (Advanced)

If you want more control over the deployment process, you can use GitHub Actions:

1. Create `.github/workflows/deploy.yml`:
   ```yaml
   name: Deploy to GitHub Pages
   
   on:
     push:
       branches: [ main ]
   
   jobs:
     deploy:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v2
         - name: Deploy to GitHub Pages
           uses: peaceiris/actions-gh-pages@v3
           with:
             github_token: ${{ secrets.GITHUB_TOKEN }}
             publish_dir: ./docs
   ```

## 🎨 Customization

### Colors
The landing page uses a modern color palette:
- Primary: `#2563eb` (Blue)
- Secondary: `#667eea` to `#764ba2` (Gradient)
- Text: `#333`, `#64748b`, `#1e293b`
- Background: `#ffffff`, `#f8fafc`

### Content
To customize the content, edit the `docs/index.html` file:
- **Hero Section**: Update the title, description, and stats
- **Features**: Modify the 6 feature cards with your specific features
- **Getting Started**: Update the installation and code examples
- **Footer**: Add or modify the footer links

### Styling
All styles are embedded in the `<style>` section of the HTML file. Key sections:
- **Header**: Navigation and logo styles
- **Hero**: Main banner with gradient background
- **Features**: Grid layout with cards
- **Getting Started**: Code blocks and examples
- **Footer**: Links and copyright

## 🔧 Local Development

To test the landing page locally:

1. **Simple HTTP Server** (Python):
   ```bash
   python -m http.server 8000
   ```
   Then visit `http://localhost:8000`

2. **Node.js HTTP Server**:
   ```bash
   npx http-server
   ```

3. **VS Code Live Server Extension**:
   - Install the "Live Server" extension
   - Right-click on `docs/index.html` and select "Open with Live Server"

## 📱 Mobile Responsiveness

The landing page is fully responsive and includes:
- Mobile-first design approach
- Responsive grid layouts
- Touch-friendly navigation
- Optimized typography for mobile screens
- Collapsible navigation for mobile devices

## 🌟 Best Practices

This landing page follows modern web development best practices:
- **Semantic HTML**: Proper use of HTML5 semantic elements
- **Accessibility**: ARIA labels, proper contrast ratios, keyboard navigation
- **Performance**: Optimized images, minimal dependencies, efficient CSS
- **SEO**: Meta tags, structured data, proper heading hierarchy

## 🤝 Contributing

If you'd like to improve the landing page:
1. Fork the repository
2. Make your changes
3. Test thoroughly on different devices
4. Submit a pull request

## 📄 License

This landing page is released under the MIT License, same as the AgentBase project.

---

For questions or support, please visit the [AgentBase GitHub repository](https://github.com/omniagents/agentbase). 