# Installation & Deployment Guide

This guide covers installing dependencies and deploying the RailDevHub website.

## Prerequisites

Before you begin, ensure you have:
- **Node.js 18 or higher** - [Download here](https://nodejs.org/)
- **npm** (comes with Node.js)
- **Git** - [Download here](https://git-scm.com/)
- **GitHub account** - [Sign up here](https://github.com/)

## Local Installation

### Step 1: Install Dependencies

```bash
# Navigate to the project directory
cd /home/cevheri/projects/tcdd/raildevhub-web

# Install all dependencies
npm install
```

This will install:
- Astro 4.15+
- TailwindCSS 3.4+
- TypeScript
- All required dependencies

### Step 2: Start Development Server

```bash
# Start the development server
npm run dev
```

The website will be available at: **http://localhost:4321**

### Step 3: Verify Installation

Open your browser and navigate to `http://localhost:4321`. You should see:
- ✅ Home page with hero section
- ✅ Navigation menu (Home, About, Expertise, Projects)
- ✅ Responsive design on mobile devices
- ✅ All pages accessible

## Building for Production

### Create Production Build

```bash
# Build the site
npm run build
```

This creates an optimized production build in the `dist/` folder.

### Preview Production Build

```bash
# Preview the production build locally
npm run preview
```

The production preview will be available at: **http://localhost:4321**

## Deployment to GitHub Pages

### Option 1: Automatic Deployment (Recommended)

#### Step 1: Create GitHub Repository

```bash
# Initialize git repository (if not already initialized)
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: RailDevHub website"
```

#### Step 2: Create GitHub Repository Online

1. Go to [GitHub](https://github.com/new)
2. Repository name: `raildevhub.github.io` (or your desired name)
3. Make it **public**
4. **Do NOT** initialize with README (we already have one)
5. Click "Create repository"

#### Step 3: Push to GitHub

```bash
# Add GitHub remote (replace with your repository URL)
git remote add origin https://github.com/raildevhub/raildevhub.github.io.git

# Push to main branch
git branch -M main
git push -u origin main
```

#### Step 4: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** tab
3. Click **Pages** in the left sidebar
4. Under "Source", select **GitHub Actions**
5. The workflow is already configured in `.github/workflows/deploy.yml`

#### Step 5: Wait for Deployment

- GitHub Actions will automatically build and deploy your site
- Check the **Actions** tab to see deployment progress
- Once complete (green checkmark), your site is live!

#### Step 6: Access Your Site

Your website will be available at:
```
https://raildevhub.github.io
```

Or if you used a different repository name:
```
https://[your-username].github.io/[repository-name]
```

### Option 2: Manual Deployment

If you prefer manual deployment:

```bash
# Build the site
npm run build

# The 'dist' folder contains your site
# Upload contents of 'dist' folder to your hosting provider
```

## Custom Domain (Optional)

To use a custom domain like `raildevhub.com`:

### Step 1: Add CNAME File

Create `public/CNAME` file with your domain:
```
raildevhub.com
```

### Step 2: Configure DNS

Add these DNS records at your domain provider:

**For apex domain (raildevhub.com):**
```
A    185.199.108.153
A    185.199.109.153
A    185.199.110.153
A    185.199.111.153
```

**For www subdomain:**
```
CNAME    www    raildevhub.github.io
```

### Step 3: Configure in GitHub

1. Go to repository **Settings** → **Pages**
2. Enter your custom domain
3. Check "Enforce HTTPS"
4. Save

**Note:** DNS propagation can take up to 24-48 hours.

## Updating the Site

### Make Changes Locally

```bash
# 1. Make your changes to the files
# 2. Test locally
npm run dev

# 3. Build to verify
npm run build
```

### Deploy Changes

```bash
# Commit your changes
git add .
git commit -m "Update: description of changes"

# Push to GitHub
git push
```

GitHub Actions will automatically deploy your changes!

## Troubleshooting

### Issue: npm install fails

**Solution:**
```bash
# Clear npm cache
npm cache clean --force

# Delete node_modules and package-lock.json
rm -rf node_modules package-lock.json

# Reinstall
npm install
```

### Issue: Port 4321 already in use

**Solution:**
```bash
# Use a different port
npm run dev -- --port 3000
```

### Issue: GitHub Actions deployment fails

**Solution:**
1. Check the Actions tab for error messages
2. Verify `astro.config.mjs` has correct `site` URL
3. Ensure repository is public
4. Check that GitHub Pages is enabled in Settings

### Issue: CSS not loading on GitHub Pages

**Solution:**
Ensure `astro.config.mjs` has the correct `site` configuration:
```javascript
export default defineConfig({
  site: 'https://raildevhub.github.io',
  // ...
});
```

### Issue: 404 on navigation

**Solution:**
GitHub Pages serves `index.html` files. Astro automatically handles this, but ensure:
- Pages are in `src/pages/` as `.astro` files
- Navigation links don't have `.html` extension
- Build completed successfully

## Environment Verification

### Check Node Version
```bash
node --version
# Should be 18.0.0 or higher
```

### Check npm Version
```bash
npm --version
# Should be 8.0.0 or higher
```

### Check Git Version
```bash
git --version
# Should be 2.0.0 or higher
```

## Performance Optimization

The site is already optimized, but you can:

### 1. Optimize Images
```bash
# Install image optimization tool
npm install --save-dev @astrojs/image

# Use in your .astro files
```

### 2. Enable Caching
GitHub Pages automatically handles caching for static assets.

### 3. Monitor Performance
Use [PageSpeed Insights](https://pagespeed.web.dev/) to test your live site.

## Security Considerations

- ✅ No server-side code (static site = more secure)
- ✅ HTTPS enforced on GitHub Pages
- ✅ No database or API keys required
- ✅ No user data collection

## Backup Recommendations

Your code is backed up on GitHub, but also consider:
1. Keep a local copy of the repository
2. Tag important versions: `git tag v1.0.0`
3. Regular commits with clear messages

## Getting Help

If you encounter issues:

1. **Check Documentation**
   - README.md
   - QUICKSTART.md
   - This file (INSTALL.md)

2. **Official Resources**
   - Astro Docs: https://docs.astro.build
   - GitHub Pages: https://pages.github.com
   - TailwindCSS: https://tailwindcss.com

3. **Community Support**
   - Astro Discord: https://astro.build/chat
   - Stack Overflow: Tag with `astro` or `github-pages`

## Success Checklist

Before going live, verify:

- [ ] All pages load correctly
- [ ] Navigation works on all pages
- [ ] Mobile responsive design works
- [ ] All links are functional
- [ ] Images load properly (if added)
- [ ] Content is accurate and up-to-date
- [ ] No console errors in browser
- [ ] GitHub Actions deployment successful
- [ ] Custom domain configured (if applicable)
- [ ] HTTPS is enforced

## Post-Deployment

After successful deployment:

1. **Test Live Site** - Visit your GitHub Pages URL
2. **Check All Pages** - Navigate through all sections
3. **Mobile Testing** - Test on phone/tablet
4. **Share** - Share your new website!
5. **Monitor** - Check GitHub Actions for any issues

---

**Congratulations! Your RailDevHub website is now live! 🚀**
