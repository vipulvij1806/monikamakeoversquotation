# Deployment Guide

This guide covers deploying the Quotation Builder to various platforms.

## Table of Contents
- [GitLab Pages](#gitlab-pages)
- [Vercel](#vercel)
- [Netlify](#netlify)
- [Self-Hosted](#self-hosted)

---

## GitLab Pages

### Option 1: Automatic Deployment (Recommended)

The project includes `.gitlab-ci.yml` for automatic CI/CD:

1. **Push to GitLab**
   ```bash
   git push origin main
   ```

2. **CI/CD Pipeline Runs Automatically**
   - GitLab CI builds your app
   - Deploys to GitLab Pages
   - Available at: `https://yourusername.gitlab.io/quotation-builder`

3. **Access Your App**
   - Open `https://yourusername.gitlab.io/quotation-builder`
   - Share the link with clients

### Option 2: Manual Deployment

1. **Build Locally**
   ```bash
   npm run build
   ```

2. **Upload to GitLab Pages**
   - Go to your GitLab project
   - Settings → Pages
   - Upload `dist/` folder contents

---

## Vercel

### Quick Deploy (30 seconds)

1. **Visit Vercel**
   - Go to [vercel.com](https://vercel.com)
   - Sign in with GitHub/GitLab/Bitbucket

2. **Create New Project**
   - Click "Import Project"
   - Select your repository
   - Vercel auto-detects it's a Vite project

3. **Deploy**
   - Click "Deploy"
   - Wait 1-2 minutes
   - Your app is live!

4. **Custom Domain** (optional)
   - Settings → Domains
   - Add your custom domain

### Environment Variables
In Vercel Dashboard:
```
VITE_BUSINESS_NAME=Your Business
VITE_BUSINESS_PHONE=+91-XXXXX-XXXXX
VITE_BUSINESS_EMAIL=your-email@example.com
```

---

## Netlify

### Option 1: Drag & Drop

1. **Build Locally**
   ```bash
   npm run build
   ```

2. **Go to Netlify**
   - Visit [netlify.com](https://netlify.com)
   - Drag-and-drop the `dist/` folder
   - Your app is live in 10 seconds!

### Option 2: Git Integration

1. **Connect GitHub/GitLab**
   - Click "New site from Git"
   - Select your repository

2. **Build Settings**
   - Build command: `npm run build`
   - Publish directory: `dist`

3. **Deploy**
   - Netlify deploys automatically on push
   - Get a URL like: `https://quotation-builder-xyz.netlify.app`

4. **Custom Domain** (optional)
   - Domain settings → Add custom domain

---

## Self-Hosted

### Prerequisites
- Server with nginx, Apache, or Node.js
- SSH access or file upload capability
- Domain name (optional)

### Deployment Steps

#### Option 1: Static File Server (nginx)

1. **Build Your App**
   ```bash
   npm run build
   ```

2. **Upload to Server**
   ```bash
   # SCP example
   scp -r dist/* user@yourserver.com:/var/www/quotation-builder/
   ```

3. **Configure nginx**
   ```nginx
   server {
       listen 80;
       server_name yourdomain.com;

       root /var/www/quotation-builder;
       index index.html;

       location / {
           try_files $uri $uri/ /index.html;
       }
   }
   ```

4. **Restart nginx**
   ```bash
   sudo systemctl restart nginx
   ```

#### Option 2: Apache

1. **Build Your App**
   ```bash
   npm run build
   ```

2. **Upload to Server**
   ```bash
   scp -r dist/* user@yourserver.com:/var/www/html/quotation-builder/
   ```

3. **Create .htaccess**
   ```apache
   <IfModule mod_rewrite.c>
     RewriteEngine On
     RewriteCond %{REQUEST_FILENAME} !-f
     RewriteCond %{REQUEST_FILENAME} !-d
     RewriteRule ^ index.html [QSA,L]
   </IfModule>
   ```

4. **Restart Apache**
   ```bash
   sudo systemctl restart apache2
   ```

#### Option 3: Docker

Create `Dockerfile`:
```dockerfile
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

Build and run:
```bash
docker build -t quotation-builder .
docker run -p 80:80 quotation-builder
```

---

## Domain Configuration

### SSL Certificate (HTTPS)

#### For GitLab Pages
- Automatic via Let's Encrypt
- No additional steps needed

#### For Vercel
- Automatic via Let's Encrypt
- Included free with all plans

#### For Netlify
- Automatic via Let's Encrypt
- Free for custom domains

#### For Self-Hosted
```bash
# Using Certbot (nginx)
sudo certbot --nginx -d yourdomain.com

# Using Certbot (Apache)
sudo certbot --apache -d yourdomain.com
```

---

## Environment-Specific Configuration

### Production vs. Development

Create separate config files:
- `src/config/business-config.json` - Global config
- `.env.local` - Local environment variables
- `.env.production` - Production variables

### Update for Each Environment

**For GitLab Pages:**
- Project ID: `yourusername/quotation-builder`
- URL: `https://yourusername.gitlab.io/quotation-builder`

**For Vercel:**
- Project name: `quotation-builder`
- URL: `https://quotation-builder.vercel.app`

**For Netlify:**
- Site name: `quotation-builder`
- URL: `https://quotation-builder.netlify.app`

**For Self-Hosted:**
- Domain: `yourdomain.com`
- URL: `https://yourdomain.com`

---

## Monitoring & Maintenance

### Check Deployment Status

**GitLab:**
- CI/CD → Pipelines → View logs

**Vercel:**
- Deployments → View build logs

**Netlify:**
- Deploys → Click deployment → View logs

### Update Code

All platforms auto-deploy when you push to main branch:
```bash
# Make changes
git add .
git commit -m "Update business info"
git push origin main

# Your changes are live in 1-2 minutes!
```

### Rollback to Previous Version

**GitLab Pages:**
- CI/CD → Pipelines → Select previous pipeline → Retry

**Vercel:**
- Deployments → Select previous deployment → Promote to Production

**Netlify:**
- Deploys → Click previous deploy → Publish deploy

---

## Performance Optimization

### Lighthouse Scores
- Audit your deployed site
- All platforms should score 90+

### Caching
- GitLab Pages: Browser cache headers configured
- Vercel: Automatic edge caching
- Netlify: Automatic CDN caching

### Loading Speed
- Vite already optimizes for speed
- All platforms use global CDNs
- First load: < 2 seconds

---

## Troubleshooting

### App shows blank page
```bash
# Check browser console for errors
# Ensure dist/index.html is deployed
# Verify path configuration
```

### Styles not loading
```bash
# Re-run build
npm run build

# Re-deploy dist/ folder
```

### PDF generation fails
```bash
# Check browser console logs
# Verify localhost permissions (CORS)
# Test in latest Chrome/Firefox
```

---

## Security

### Protect Your Quotations
- All data stored locally in browser
- Nothing sent to servers (except for PDF generation)
- No database = no breaches

### Enable HTTPS
- All platforms provide free SSL
- Always use HTTPS URLs
- Share secure links with clients

### Keep Dependencies Updated
```bash
# Monthly
npm update
npm audit fix
git push
```

---

## Support

For platform-specific issues:
- **GitLab Pages:** [docs.gitlab.com/ee/user/project/pages/](https://docs.gitlab.com/ee/user/project/pages/)
- **Vercel:** [vercel.com/docs](https://vercel.com/docs)
- **Netlify:** [docs.netlify.com](https://docs.netlify.com)

---

**Choose the platform that works best for you!** 

- **GitLab Pages:** Free, integrated with GitLab, easiest setup
- **Vercel:** Free tier, great for Next.js projects, excellent performance
- **Netlify:** Free tier, great user experience, automatic deploys
- **Self-Hosted:** Full control, can be cheaper at scale

All options are production-ready and suitable for client use.
