# Quotation Builder - Dynamic Quotation Generator for Makeup Artists

A fully customizable, web-based quotation builder for makeup artistry services. Create professional, branded PDF quotations in minutes with real-time calculations, flexible pricing, and drag-and-drop service management.

## ✨ Features

### Core Features
- ✅ **Step-by-Step Client Intake** - Collect client details in 3 intuitive steps
- ✅ **Individual Service Selection** - Choose from Bridal, Party Makeup, Salon Setup, and Additional Services
- ✅ **Flexible Pricing** - Mix different service categories with custom pricing
- ✅ **Real-Time Calculations** - Automatic price updates with discount application
- ✅ **Drag-and-Drop Reordering** - Arrange services by date or in custom order
- ✅ **Professional PDF Generation** - Branded, polished quotation PDFs
- ✅ **Data Export** - Save quotations as JSON for backup and portability
- ✅ **Fully Customizable** - Update services, pricing, and branding without code

### Service Categories
1. **Bridal Events** - Individual selection: Haldi, Mehandi, Sangeet, Cocktail, Wedding, Engagement
2. **Party Makeups** - Flexible categories with guest count: HD, Basic, Other
3. **Salon Setup** - Per Artist or Per Guest costs
4. **Additional Services** - Hair Extensions, Fresh Flowers, Hair Accessories, Conveyance, Custom

### Discount Management
- Service-level discounts (individual pricing)
- Quotation-level discounts (percentage or fixed amount)
- Bulk discount rules (auto-apply for multiple events)
- Real-time discount tracking and visualization

## 🚀 Quick Start

### Prerequisites
- Node.js 16+ 
- npm or yarn

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/quotation-builder.git
cd quotation-builder

# Install dependencies
npm install

# Create environment file
cp .env.example .env.local

# Start development server
npm run dev
```

The app will open at `http://localhost:3000`

### First-Time Setup

1. **Customize Business Info**
   - Edit `src/config/business-config.json`
   - Update: businessName, logo, contact, colors

2. **Configure Services**
   - Edit `src/config/services-config.json`
   - Add/modify services and pricing

3. **Test a Quotation**
   - Fill in client details (3 steps)
   - Select services from categories
   - Generate PDF to verify branding

## 📁 Project Structure

```
quotation-builder/
├── public/                          # Static assets
├── src/
│   ├── components/
│   │   ├── Intake/                  # Client information (3-step flow)
│   │   │   ├── Step1BasicInfo.jsx
│   │   │   ├── Step2Location.jsx
│   │   │   ├── Step3Confirmation.jsx
│   │   │   └── IntakeFlow.jsx
│   │   ├── ServiceSelection/        # Service forms (Bridal, Party, Salon, Additional)
│   │   │   ├── BridalEventsForm.jsx
│   │   │   ├── PartyMakeupsForm.jsx
│   │   │   ├── SalonSetupForm.jsx
│   │   │   └── AdditionalServicesForm.jsx
│   │   ├── QuotationSummary/        # Service list & pricing
│   │   │   ├── ServiceItem.jsx
│   │   │   └── QuotationSummary.jsx
│   │   └── PDFTemplate/
│   │       └── PDFTemplate.jsx
│   ├── hooks/
│   │   └── useQuotation.js          # State management
│   ├── utils/
│   │   ├── calculations.js          # Price calculations
│   │   └── pdfGenerator.js          # PDF export logic
│   ├── config/
│   │   ├── business-config.json     # 🔧 CUSTOMIZE: Business info
│   │   └── services-config.json     # 🔧 CUSTOMIZE: Services & pricing
│   ├── App.jsx                      # Main component
│   ├── App.css                      # Global styles
│   └── index.jsx                    # React entry point
├── index.html                       # HTML template
├── package.json                     # Dependencies
├── vite.config.js                   # Vite config
├── tailwind.config.js               # TailwindCSS config
├── .env.example                     # Environment template
└── README.md                        # This file
```

## 🎨 Customization Guide

### Edit Business Information

**File:** `src/config/business-config.json`

```json
{
  "businessName": "Your Business Name",
  "tagline": "YOUR TAGLINE",
  "logoUrl": "/your-logo.png",
  "contact": {
    "phone": "+91-XXXXX-XXXXX",
    "email": "your-email@example.com"
  },
  "colors": {
    "primary": "#534AB7",
    "secondary": "#1D9E75",
    "accent": "#D85A30",
    "text": "#2C2C2A"
  }
}
```

### Add or Edit Services

**File:** `src/config/services-config.json`

**Add a new bridal event:**
```json
{
  "id": "haldi",
  "name": "Haldi Makeup",
  "defaultPrice": 4500,
  "inclusions": ["Makeup", "Hairstyle", "Draping"],
  "exclusions": ["Fresh flowers"],
  "notes": "Traditional haldi look"
}
```

**Add a new category:**
```json
{
  "id": "new-category",
  "name": "Category Name",
  "description": "Category description",
  "services": [
    { /* service objects */ }
  ]
}
```

### Upload Your Logo

1. Place logo in `public/` folder
2. Update path in `business-config.json`:
```json
"logoUrl": "/your-logo.png"
```

### Customize Colors

In `business-config.json`, update the `colors` object:
```json
"colors": {
  "primary": "#YOUR_HEX_COLOR",
  "secondary": "#YOUR_HEX_COLOR",
  "accent": "#YOUR_HEX_COLOR",
  "text": "#YOUR_HEX_COLOR"
}
```

## 💻 Technology Stack

- **Frontend Framework:** React 18
- **Build Tool:** Vite
- **Styling:** TailwindCSS
- **PDF Generation:** jsPDF + html2canvas
- **Drag & Drop:** React Beautiful DnD (optional enhancement)
- **Date Handling:** date-fns

## 📝 Usage Workflow

### Step 1: Client Intake (3 steps)
1. Enter client name and contact number
2. Enter event date and location
3. Review and confirm details

### Step 2: Service Selection
- Choose from 4 service categories
- Fill in service-specific details
- Add services to quotation

### Step 3: Quotation Management
- Review selected services (grouped by date)
- Apply service-level or quotation-level discounts
- Reorder services (by date or custom)
- View real-time pricing updates

### Step 4: Generate & Export
- Generate professional PDF
- Export as JSON for backup
- Share with clients

## 🎯 Features in Detail

### Individual Service Selection
Unlike template-based quotations, each service is individually selectable:
- **Bridal Events:** Select specific events (Haldi, Mehandi, Wedding, etc.)
- **Party Makeups:** Choose category + guest count + price per guest
- **Salon Setup:** Pick setup type + count + unit price
- **Additional Services:** Add custom or predefined add-ons

### Flexible Pricing
- Base pricing set per service
- Override with individual service discounts
- Apply quotation-level discounts (percentage or amount)
- Real-time calculations for party makeup by guest count

### Date-Based Organization
- Services automatically grouped by event date
- Toggle between date-sorted view and custom order
- Drag-and-drop to reorder within or across dates

### Professional PDFs
- Branded with business logo and colors
- Client information prominently displayed
- Itemized service breakdown
- Pricing summary with discount details
- Inclusions and exclusions listed
- Payment terms and contact info in footer

## 🔄 Data Management

### Save Quotation
Quotations are auto-saved to browser's localStorage as you build them.

### Export as JSON
Export current quotation as JSON file for backup:
```json
{
  "clientDetails": { /* ... */ },
  "services": [ /* ... */ ],
  "pricingSummary": { /* ... */ }
}
```

### Import from JSON
Load previously saved quotation JSON file to continue editing.

## 🛠️ Configuration

### Environment Variables
Create `.env.local` file:
```env
VITE_BUSINESS_NAME=Your Business Name
VITE_BUSINESS_TAGLINE=Your Tagline
VITE_BUSINESS_PHONE=+91-XXXXX-XXXXX
VITE_BUSINESS_EMAIL=contact@example.com
```

## 🚀 Deployment

### Deploy to Vercel (Recommended)
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel
```

### Deploy to Netlify
```bash
# Build for production
npm run build

# Drag-and-drop `dist` folder to netlify.com
```

### Deploy to GitHub Pages
```bash
npm run build
# Push `dist` folder to gh-pages branch
```

### Self-Hosted
```bash
npm run build
# Upload `dist` folder to your server
# Serve with any static file server (nginx, Apache, etc.)
```

## 📱 Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (responsive design)

## 🔒 Data Privacy

- **No Backend Required:** All data stored locally in browser
- **No Cloud Sync (by default):** Users have full control
- **Local Storage:** Quotations saved in browser localStorage
- **Optional Backup:** Export as JSON for external backup

## 📚 Scripts

```bash
# Development
npm run dev          # Start dev server with hot reload

# Production
npm run build        # Build optimized distribution
npm run preview      # Preview production build locally

# Code Quality
npm run lint         # Lint code (if eslint configured)
```

## 🐛 Troubleshooting

### Logo not appearing in PDF
- Check file exists in `public/` folder
- Verify correct path in `business-config.json`
- Ensure file is PNG/JPG format

### PDF looks different from preview
- Zoom browser to 100% before generating PDF
- Check print preview in browser
- Verify color values in `business-config.json`

### Quotation not saving
- Check browser's localStorage is enabled
- Try exporting as JSON manually
- Clear browser cache and reload

### Services not appearing
- Verify `services-config.json` is valid JSON
- Check service IDs match between components
- Restart dev server after config changes

## 📖 Documentation

- **CUSTOMIZATION.md** - Detailed customization guide
- **DEPLOYMENT.md** - Deployment instructions
- **CONTRIBUTING.md** - Contribution guidelines
- **Planning Documents** (in docs/) - System architecture and design

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see LICENSE file for details.

This means you can:
- ✅ Use it for personal or commercial purposes
- ✅ Modify and customize it
- ✅ Distribute and share it
- ✅ Use it in private or public projects

Just remember to credit the original project!

## 🙏 Acknowledgments

- Built with React, Vite, and TailwindCSS
- PDF generation powered by jsPDF and html2canvas
- Inspired by professional quotation builders

## 📞 Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Check existing documentation
- Review the planning documents in `/docs`

## 🚀 Roadmap

### Phase 1: Current (MVP)
- ✅ Step-by-step client intake
- ✅ Service selection
- ✅ PDF generation
- ✅ JSON export

### Phase 2: Planned
- Quotation templates (save/reuse frequent quotations)
- Multiple PDF design themes
- Advanced discount rules
- Analytics dashboard

### Phase 3: Planned
- Cloud backup (Firebase integration)
- Client portal (view/approve quotations)
- Payment integration (Razorpay/Stripe)
- Mobile app

## 💬 Feedback

Love this project? Have suggestions?
- Star the repository ⭐
- Share with other makeup artists
- Provide feedback via issues

---

**Made with ❤️ for Makeup Artists**

Start using Quotation Builder today and save time creating professional quotations!
