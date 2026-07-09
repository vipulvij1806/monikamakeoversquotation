# Setup & Customization Guide

Complete step-by-step guide to set up the Quotation Builder for GitLab/GitHub and customize it for your business.

## Table of Contents
1. [Initial Setup](#initial-setup)
2. [Customize Business Information](#customize-business-information)
3. [Configure Services](#configure-services)
4. [Upload Logo](#upload-logo)
5. [Customize Colors](#customize-colors)
6. [Deploy to GitLab](#deploy-to-gitlab)
7. [Test Your App](#test-your-app)

---

## Initial Setup

### Step 1: Clone or Fork Repository

**Option A: Your Own Repository**
```bash
# Clone the quotation-builder as template
git clone https://github.com/quotation-builder/quotation-builder.git
cd quotation-builder

# Remove original remote
git remote remove origin

# Add your repository
git remote add origin https://gitlab.com/yourusername/quotation-builder.git

# Push to your repo
git push -u origin main
```

**Option B: Fork on GitLab**
1. Go to GitLab
2. Click "New project"
3. Select "Import project"
4. Enter the repository URL
5. Click "Create project"

### Step 2: Install Dependencies

```bash
# Install Node.js dependencies
npm install

# This installs:
# - React (UI framework)
# - Vite (build tool)
# - TailwindCSS (styling)
# - jsPDF (PDF generation)
# - html2canvas (PDF rendering)
```

### Step 3: Create Environment File

```bash
# Copy example to local
cp .env.example .env.local

# Edit with your information
nano .env.local
# or
code .env.local
```

---

## Customize Business Information

### File: `src/config/business-config.json`

Open the file and update the following sections:

#### 1. Business Name & Tagline

```json
{
  "businessName": "Your Business Name",
  "tagline": "YOUR TAGLINE"
}
```

Examples:
- `"businessName": "Priya's Makeup Studio"`
- `"tagline": "PROFESSIONAL MAKEUP ARTIST"`

#### 2. Contact Information

```json
{
  "contact": {
    "phone": "+91-98765-43210",
    "email": "your-email@example.com",
    "website": "https://yourwebsite.com"
  }
}
```

#### 3. Location

```json
{
  "location": {
    "city": "Your City",
    "state": "Your State",
    "country": "India"
  }
}
```

#### 4. Terms & Conditions

```json
{
  "termsAndConditions": "Payment required 7 days before event. Quotation valid for 30 days."
}
```

#### 5. Default Inclusions

```json
{
  "defaultInclusions": [
    "Makeup",
    "Hairstyle",
    "Draping",
    "Lenses",
    "False Lashes"
  ]
}
```

#### 6. Default Exclusions

```json
{
  "defaultExclusions": [
    "Conveyance Extra",
    "Hair Extension",
    "Fresh flowers",
    "Hair accessories"
  ]
}
```

**Example Full Config:**
```json
{
  "businessName": "Monika Makeovers",
  "tagline": "MAKEUP ARTIST",
  "logoUrl": "/logo.png",
  "contact": {
    "phone": "+91-98765-43210",
    "email": "monika@makeovers.com",
    "website": "https://monikamakeovers.com"
  },
  "location": {
    "city": "Jaipur",
    "state": "Rajasthan",
    "country": "India"
  },
  "currency": "₹",
  "termsAndConditions": "Full payment required 7 days before event. Quotation valid for 30 days.",
  "defaultInclusions": ["Makeup", "Hairstyle", "Draping", "Lenses", "False Lashes"],
  "defaultExclusions": ["Conveyance Extra", "Hair Extension", "Fresh flowers"]
}
```

---

## Configure Services

### File: `src/config/services-config.json`

This file defines all your services and pricing.

### Structure Overview

```json
{
  "categories": [
    {
      "id": "category-id",
      "name": "Category Name",
      "description": "Category description",
      "services": [
        {
          "id": "service-id",
          "name": "Service Name",
          "defaultPrice": 5000,
          "inclusions": ["Makeup", "Hairstyle"],
          "exclusions": ["Hair Extension"],
          "notes": "Special notes"
        }
      ]
    }
  ]
}
```

### Category 1: Bridal Events

**Add New Bridal Event:**
```json
{
  "id": "reception",
  "name": "Reception Makeup",
  "defaultPrice": 7500,
  "inclusions": ["Makeup", "Hairstyle", "Draping", "False Lashes"],
  "exclusions": ["Fresh flowers", "Hair Extension"],
  "notes": "Glamorous evening reception look"
}
```

**Edit Existing Event:**
- Change `defaultPrice` to update cost
- Update `inclusions`/`exclusions` as needed
- Modify notes for specific details

### Category 2: Party Makeups

**Structure:**
```json
{
  "id": "party-hd",
  "name": "HD Makeup",
  "pricePerGuest": 2500,
  "inclusions": ["Makeup", "Hairstyle", "Draping"],
  "exclusions": ["Hair Extension"],
  "category": "HD"
}
```

**Edit Prices:**
- Update `pricePerGuest` value
- Price is multiplied by guest count automatically

### Category 3: Salon Setup

**Structure:**
```json
{
  "id": "salon-per-artist",
  "name": "Per Artist Cost",
  "pricePerUnit": 1500,
  "notes": "Covers one makeup artist's setup"
}
```

### Category 4: Additional Services

**Add New Add-on:**
```json
{
  "id": "hair-extensions-premium",
  "name": "Premium Hair Extensions",
  "defaultPrice": 2000,
  "notes": "High-quality extensions for long-lasting wear"
}
```

---

## Upload Logo

### Step 1: Prepare Your Logo

1. Size: ~400x200 pixels (landscape)
2. Format: PNG or JPG
3. Background: Transparent PNG preferred
4. Quality: High resolution (300+ DPI)

### Step 2: Upload File

```bash
# Copy your logo to public folder
cp /path/to/your-logo.png ./public/logo.png
```

### Step 3: Update Config

In `src/config/business-config.json`:
```json
{
  "logoUrl": "/logo.png"
}
```

---

## Customize Colors

### Edit Color Scheme

In `src/config/business-config.json`, find the `colors` object:

```json
{
  "colors": {
    "primary": "#534AB7",    // Main brand color (headings, buttons)
    "secondary": "#1D9E75",  // Accent color (highlights)
    "accent": "#D85A30",     // Tertiary color (special emphasis)
    "text": "#2C2C2A",       // Default text color
    "border": "#B4B2A9"      // Border and divider color
  }
}
```

### Choose Your Colors

**Option 1: Use Hex Codes**

Get hex codes from:
- [colorpicker.com](https://www.colorpicker.com)
- [coolors.co](https://coolors.co)
- Design tools (Photoshop, Figma, etc.)

**Option 2: Color Palettes**

**Elegant Purple:**
```json
{
  "primary": "#6366F1",      // Indigo
  "secondary": "#10B981",    // Green
  "accent": "#F59E0B",       // Amber
  "text": "#1F2937",         // Dark gray
  "border": "#E5E7EB"        // Light gray
}
```

**Rose Gold:**
```json
{
  "primary": "#B8336A",      // Rose
  "secondary": "#D4A574",    // Gold
  "accent": "#E8A38D",       // Dusty rose
  "text": "#2C2C2C",         // Dark
  "border": "#D9CAC3"        // Light
}
```

**Modern Teal:**
```json
{
  "primary": "#0D9488",      // Teal
  "secondary": "#7C3AED",    // Violet
  "accent": "#EC4899",       // Pink
  "text": "#0F172A",         // Almost black
  "border": "#CBDACF"        // Pale
}
```

---

## Deploy to GitLab

### Step 1: Push to GitLab

```bash
# Make sure everything is committed
git add .
git commit -m "Customize for your business"

# Push to GitLab
git push -u origin main
```

### Step 2: Enable GitLab Pages

1. Go to your GitLab project
2. Settings → Pages
3. Under "Build, test, and deploy" section
4. Check "Shared runners" is enabled
5. Pipeline will run automatically

### Step 3: Access Your App

Your app is available at:
```
https://yourusername.gitlab.io/quotation-builder
```

For custom domain:
1. Settings → Pages
2. Add your custom domain
3. Follow DNS instructions
4. Update business config with new URL

---

## Test Your App

### Test Locally (Before Deploying)

```bash
# Start development server
npm run dev

# Open in browser
# http://localhost:3000
```

### Test Workflow

1. **Intake Flow**
   - Enter client name: "Test Client"
   - Phone: "9876543210"
   - Event date: Today or tomorrow
   - Location: "Test City"
   - Requirements: "Test requirements"
   - Click Next through all steps

2. **Service Selection**
   - Click "Bridal Events"
   - Select "Haldi Makeup"
   - Verify price matches config
   - Click "Add Service"

3. **Add More Services**
   - Add "Party Makeup" with 15 guests
   - Add "Salon Setup"
   - Verify prices calculate correctly

4. **PDF Generation**
   - Click "Generate PDF"
   - Verify logo appears
   - Check colors match config
   - Verify pricing is correct
   - Check client info is filled in

5. **Test on Mobile**
   - Open on phone browser
   - Test responsive design
   - Verify forms work on small screens

---

## Verification Checklist

- [ ] Business name changed in config
- [ ] Logo uploaded and displaying
- [ ] Contact information updated
- [ ] Color scheme customized
- [ ] Services updated with your pricing
- [ ] Inclusions/Exclusions match your services
- [ ] All fields in business-config.json are valid JSON
- [ ] App runs locally without errors
- [ ] PDF generates with correct branding
- [ ] Deployed to GitLab Pages successfully
- [ ] GitLab Pages URL is accessible
- [ ] App works on mobile browser

---

## Next Steps

### After Customization

1. **Share with Team** (if any)
   - GitLab project URL
   - Instructions for updates

2. **Backup Configuration**
   ```bash
   # Export your config
   cp src/config/business-config.json business-config-backup.json
   cp src/config/services-config.json services-config-backup.json
   ```

3. **Create Quotations**
   - Test by creating real quotations
   - Share PDFs with clients
   - Gather feedback

4. **Update Pricing** (as needed)
   - Edit services-config.json
   - Commit and push
   - Changes deploy automatically

---

## Troubleshooting

### Logo not appearing
```bash
# Check file exists
ls -la public/logo.png

# Verify path in config
# Should be: "logoUrl": "/logo.png"
```

### Colors not changing
```bash
# Clear browser cache
# Ctrl+Shift+Delete (Chrome) or Cmd+Shift+Delete (Mac)

# Verify JSON is valid
# Use online JSON validator
```

### App won't start
```bash
# Check for syntax errors
npm run lint

# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install
npm run dev
```

### PDF generation fails
```bash
# Check browser console (F12)
# Verify permissions
# Try different browser
```

---

## Support

- **Issues:** Check README.md Troubleshooting section
- **Questions:** Open a GitHub/GitLab issue
- **Help:** Review the planning documents

---

**You're all set!** Your quotation builder is ready to use! 🎉
