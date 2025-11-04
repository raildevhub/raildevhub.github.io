# Quick Start Guide

Welcome to the RailDevHub website project! This guide will help you get up and running quickly.

## Installation & First Run

```bash
# 1. Install dependencies
npm install

# 2. Start the development server
npm run dev

# 3. Open your browser to http://localhost:4321
```

That's it! The website should now be running locally.

## Project Overview

This is a modern, professional corporate website built with:
- **Astro** for fast static site generation
- **TailwindCSS** for beautiful, responsive styling
- **TypeScript** for type safety

## Website Pages

The website includes 4 main pages:

1. **Home (`/`)** - Hero section, core values, technology preview, and CTAs
2. **About (`/about`)** - Team mission, values, and domain focus
3. **Expertise (`/expertise`)** - Detailed AI and software engineering technologies
4. **Projects (`/projects`)** - DDYS and Resource Planning platform showcases

## Making Changes

### Editing Content

All page content is in the `src/pages/` directory:
- `src/pages/index.astro` - Home page
- `src/pages/about.astro` - About page
- `src/pages/expertise.astro` - Expertise page
- `src/pages/projects.astro` - Projects page

### Editing Components

Reusable components are in `src/components/`:
- `Header.astro` - Navigation header
- `Footer.astro` - Site footer

### Editing Styles

- Global styles: `src/styles/global.css`
- TailwindCSS config: `tailwind.config.mjs`
- Color scheme: Defined in `tailwind.config.mjs` under `extend.colors`

## Building for Production

```bash
# Build the site
npm run build

# Preview the production build
npm run preview
```

The built site will be in the `dist/` folder.

## Deploying to GitHub Pages

1. Create a GitHub repository named `raildevhub.github.io`
2. Push this code to the `main` branch
3. Enable GitHub Pages in repository settings:
   - Go to Settings > Pages
   - Source: GitHub Actions
4. The site will automatically deploy on every push to `main`

## Customization Tips

### Changing Colors

Edit `tailwind.config.mjs` to change the color palette:

```javascript
colors: {
  primary: {
    // Your color values here
  },
  railway: {
    steel: '#2c3e50',
    track: '#34495e',
    signal: '#e74c3c',
    safety: '#f39c12',
  }
}
```

### Adding New Pages

1. Create a new `.astro` file in `src/pages/`
2. Add navigation link in `src/components/Header.astro`
3. The file name becomes the URL (e.g., `contact.astro` → `/contact`)

### Changing Fonts

The site uses Google Fonts (Inter & Plus Jakarta Sans). To change:
1. Edit the font imports in `src/layouts/BaseLayout.astro`
2. Update the font family in `tailwind.config.mjs`

## Troubleshooting

### Port Already in Use

If port 4321 is already in use:
```bash
npm run dev -- --port 3000
```

### Build Errors

Clear the cache and rebuild:
```bash
rm -rf node_modules .astro dist
npm install
npm run build
```

### Styling Not Updating

TailwindCSS might need a refresh:
```bash
# Stop the dev server (Ctrl+C)
# Delete .astro cache
rm -rf .astro
# Restart
npm run dev
```

## Need Help?

- **Astro Docs:** https://docs.astro.build
- **TailwindCSS Docs:** https://tailwindcss.com/docs
- **Report Issues:** Create an issue in your GitHub repository

## Next Steps

1. Customize the content to match your exact requirements
2. Add more pages if needed (e.g., contact, blog)
3. Update the GitHub repository URLs in the footer
4. Add your own images/assets to the `public/` folder
5. Configure your domain name (if not using github.io)

Happy coding!
