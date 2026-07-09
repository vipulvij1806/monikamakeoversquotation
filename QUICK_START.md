# ⚡ Quick Start Guide (5 Minutes)

Get your quotation builder up and running on GitLab in 5 minutes!

## Prerequisites
- Node.js 16+ installed
- GitLab account
- Code editor (VS Code recommended)

---

## Step 1: Clone & Setup (2 minutes)

```bash
# Clone this repository
git clone https://gitlab.com/yourusername/quotation-builder.git
cd quotation-builder

# Install dependencies
npm install

# Copy environment template
cp .env.example .env.local
```

## Step 2: Customize (2 minutes)

### Edit Your Business Info
```bash
# Open with your editor
code src/config/business-config.json
```

Change these lines:
```json
{
  "businessName": "Your Business Name",
  "tagline": "YOUR TAGLINE",
  "contact": {
    "phone": "+91-YOUR-PHONE",
    "email": "your-email@example.com"
  }
}
```

### Edit Services & Pricing
```bash
code src/config/services-config.json
```

Update `"defaultPrice"` values to match your pricing.

### Add Your Logo
```bash
# Copy your logo to public folder
cp /path/to/your-logo.png ./public/logo.png

# Update logo path in business-config.json
# Change: "logoUrl": "/logo.png"
```

## Step 3: Test Locally (1 minute)

```bash
# Start development server
npm run dev

# Open browser to http://localhost:3000
# Click through the app to test
```

## Step 4: Deploy to GitLab Pages (No waiting!)

```bash
# Commit your changes
git add .
git commit -m "Customize for my business"
git push origin main

# GitLab CI automatically deploys!
```

Your app will be live at:
```
https://yourusername.gitlab.io/quotation-builder
```

---

## ✅ You're Done!

Your quotation builder is now live and ready to use!

### Next: Create Your First Quotation

1. Open your GitLab Pages URL
2. Fill in client details (3 steps)
3. Add services from categories
4. Generate PDF

---

## 📚 Learn More

- **Full Setup Guide:** Read [SETUP.md](SETUP.md)
- **Deployment Options:** Check [DEPLOYMENT.md](DEPLOYMENT.md)
- **Customization:** Review [README.md](README.md#-customization-guide)

---

## 🆘 Troubleshooting

### App won't start
```bash
npm install
npm run dev
```

### Logo not showing
1. Copy file to `public/logo.png`
2. Update path in `business-config.json`
3. Restart dev server

### Colors not changing
1. Edit colors in `business-config.json`
2. Clear browser cache
3. Refresh page

### PDF looks wrong
1. Verify colors in config
2. Check logo path
3. Try different browser

---

## 💡 Pro Tips

### Update Pricing Anytime
```bash
# Edit prices in services-config.json
code src/config/services-config.json

# Commit and push
git add .
git commit -m "Update pricing"
git push origin main

# Changes go live automatically!
```

### Change Business Name
```bash
# Edit business-config.json
code src/config/business-config.json

# Update businessName field
# Push to GitLab
```

### Add New Services
```bash
# Edit services-config.json
code src/config/services-config.json

# Add service to appropriate category
# Push to GitLab
```

### Share Your App
```
Your URL: https://yourusername.gitlab.io/quotation-builder

Share this link with clients to:
- View and use your quotation builder
- No installation needed
- Works on desktop, tablet, mobile
```

---

## 📞 Need Help?

1. **Check README.md** - Has detailed explanations
2. **Read SETUP.md** - Step-by-step customization
3. **Open GitLab Issue** - If something breaks

---

**That's it!** Your quotation builder is ready! 🎉

Go create some amazing quotations! 💄✨
