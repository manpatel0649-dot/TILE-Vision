# TILE-Vision
<div align="center">

<img src="https://img.shields.io/badge/Tiles%20Vision-AI-0ea5e9?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48cmVjdCB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHJ4PSI2IiBmaWxsPSIjMGVhNWU5Ii8+PHRleHQgeD0iNSIgeT0iMTciIGZvbnQtc2l6ZT0iMTQiPvCfqY88L3RleHQ+PC9zdmc+" />

# 🪟 Tiles Vision AI

### AI-Powered Tile Visualization Platform for Ceramic Showrooms

> Upload a tile or your room photo — AI generates a photorealistic interior showing exactly how any tile looks in your space. Built for ceramic showrooms to increase sales, capture leads, and impress customers.

<br/>

[![Next.js](https://img.shields.io/badge/Next.js_14-black?style=flat-square&logo=next.js&logoColor=white)](https://nextjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)](https://mongodb.com/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Claude AI](https://img.shields.io/badge/Claude_AI-D97757?style=flat-square&logo=anthropic&logoColor=white)](https://anthropic.com/)
[![Replicate](https://img.shields.io/badge/Replicate-000000?style=flat-square&logo=replicate&logoColor=white)](https://replicate.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](CONTRIBUTING.md)

<br/>

[🚀 Live Demo](https://tilesvisional.vercel.app) · [📖 Docs](#-documentation) · [🐛 Report Bug](issues) · [✨ Request Feature](issues)

<br/>

![Tiles Vision AI Banner](https://via.placeholder.com/900x400/0d1f35/0ea5e9?text=Tiles+Vision+AI+—+Preview+Screenshot)

</div>

---

## 📋 Table of Contents

- [About the Project](#-about-the-project)
- [Core Features](#-core-features)
- [How It Works](#-how-it-works)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)
  - [Running the App](#running-the-app)
- [Project Structure](#-project-structure)
- [API Reference](#-api-reference)
- [Deployment](#-deployment)
- [28-Day Build Roadmap](#-28-day-build-roadmap)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 About the Project

**Tiles Vision AI** solves the single biggest problem in every ceramic tile showroom: customers cannot visualize how a tile will actually look across an entire floor or wall before buying.

Traditional showrooms hand customers a small tile sample and ask them to *imagine* it covering their entire living room. This leads to:
- ❌ Hesitant buyers who delay or leave without purchasing
- ❌ Returns and regrets after installation
- ❌ Missed upsell opportunities for premium finishes
- ❌ No digital presence or lead capture

**Tiles Vision AI** fixes all of this with two AI-powered modes:

| Mode | How it works |
|------|-------------|
| **✨ Generate Room** | Upload a tile close-up → AI generates a brand-new photorealistic luxury interior featuring those exact tiles |
| **📷 Upload Room** | Upload your actual room photo → AI replaces the floor/wall surfaces with the chosen tile in perspective-correct, photorealistic detail |

The result: customers see exactly what they're buying — and they buy with confidence.

---

## ✨ Core Features

### 🤖 AI Visualization Engine
- **Claude Vision API** — analyzes tile texture, color, grain, and pattern to craft optimized generation prompts
- **Stable Diffusion XL** (via Replicate) — generates photorealistic room images at 1024×768 resolution
- **SAM Segmentation** — detects floor and wall surfaces in uploaded room photos automatically
- **SD Inpainting** — seamlessly replaces only the tile surfaces while preserving furniture and lighting

### 🏠 Complete Configuration Controls
- **8 Room Types** — Living Room, Bedroom, Bathroom, Kitchen, Office, Hotel Lobby, Luxury Showroom, Outdoor Area
- **3 Placement Options** — Floor only, Wall only, Full Room
- **4 Tile Sizes** — 12×12", 12×24", 24×24", Custom
- **7 Tile Finishes** — Matte, Glossy, Marble, Stone, Wooden, Ceramic, Porcelain
- **6 Tile Layouts** — Straight, Herringbone, Chevron, Brick, Diagonal, Grid
- **Custom Instructions** — free-text prompt field (400 chars) for lighting, style, and mood

### 🏪 Showroom Business Tools
- **Digital Tile Catalogue** — full browsable product library with search, filters, and QR codes
- **Lead Capture System** — captures customer name + WhatsApp on download, share, or quote request
- **Quote Generator** — auto-calculates tile quantity and estimated cost from entered room area
- **WhatsApp Integration** — sends visualization images and quote confirmations via Twilio
- **QR Codes** — every tile generates a scannable QR → opens visualizer pre-loaded with that tile

### 📊 Admin Dashboard
- Real-time summary cards: visualizations, leads, credits, top tile
- **Kanban Lead Pipeline** — New → Contacted → Quoted → Won / Lost with drag-and-drop
- **Analytics Charts** — daily trends, top tiles, conversion funnel, source breakdown
- **Tile Manager** — add, edit, bulk upload tiles via CSV
- **Automated Follow-ups** — node-cron jobs for lead reminders and customer nudges
- **PDF Reports** — auto-generated monthly analytics emailed to showroom owner

---

## 🔄 How It Works

```
Customer                    Frontend (Next.js)              Backend (Express)              AI Services
   │                              │                               │                            │
   │  Upload tile sample          │                               │                            │
   │─────────────────────────────▶│                               │                            │
   │                              │  POST /api/visualize/generate │                            │
   │                              │──────────────────────────────▶│                            │
   │                              │                               │  Send tile image to Claude │
   │                              │                               │───────────────────────────▶│
   │                              │                               │◀── Optimized prompt ───────│
   │                              │                               │                            │
   │                              │                               │  Send prompt to SDXL       │
   │                              │                               │───────────────────────────▶│
   │                              │                               │◀── Generated room URL ─────│
   │                              │                               │                            │
   │                              │◀── { imageUrl, sessionId } ───│                            │
   │◀── Photorealistic room ───────│                               │                            │
   │                              │                               │                            │
   │  Click "Request a Quote"     │                               │                            │
   │─────────────────────────────▶│  POST /api/quotes             │                            │
   │                              │──────────────────────────────▶│                            │
   │◀── WhatsApp confirmation ─────│◀──── Lead saved + WA sent ───│                            │
```

---

## 🛠 Tech Stack

### Frontend
| Technology | Purpose |
|-----------|---------|
| **Next.js 14** (App Router) | React framework, SSR, routing |
| **Tailwind CSS** | Utility-first styling |
| **Shadcn/UI** | Pre-built accessible components |
| **Zustand** | Lightweight global state management |
| **Axios** | HTTP client for API requests |
| **react-dropzone** | Drag-and-drop file uploads |
| **Recharts** | Analytics charts in admin panel |
| **react-hot-toast** | Toast notification system |

### Backend
| Technology | Purpose |
|-----------|---------|
| **Node.js + Express** | REST API server |
| **MongoDB + Mongoose** | Database and ODM |
| **JWT + bcryptjs** | Authentication and password hashing |
| **Multer** | File upload middleware |
| **Sharp** | Image processing and watermarking |
| **node-cron** | Scheduled automation jobs |
| **Helmet + express-rate-limit** | Security middleware |

### AI & Cloud Services
| Service | Purpose |
|---------|---------|
| **Anthropic Claude** (`claude-sonnet-4-5`) | Tile vision analysis + prompt engineering |
| **Replicate (SDXL)** | Photorealistic room image generation |
| **Meta SAM** (via Replicate) | Room surface segmentation |
| **SD-Inpainting** (via Replicate) | Tile surface replacement on real photos |
| **Cloudinary** | Image storage, CDN, auto-expiry |
| **Twilio WhatsApp API** | Automated customer messaging |
| **SendGrid** | Transactional email delivery |

---

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

```bash
node --version   # v18.0.0 or higher
npm --version    # v9.0.0 or higher
git --version    # any recent version
```

You also need accounts (all have free tiers) at:
- [MongoDB Atlas](https://mongodb.com/cloud/atlas) — database
- [Anthropic](https://console.anthropic.com) — Claude API
- [Replicate](https://replicate.com) — image generation
- [Cloudinary](https://cloudinary.com) — image storage
- [Twilio](https://twilio.com) — WhatsApp messaging

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/yourusername/tiles-vision-ai.git
cd tiles-vision-ai
```

**2. Install backend dependencies**
```bash
cd backend
npm install
```

**3. Install frontend dependencies**
```bash
cd ../frontend
npm install
```

### Environment Variables

**Backend** — create `backend/.env`:

```env
# Server
PORT=5000
NODE_ENV=development

# Database
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/tilesVisionAI

# Authentication
JWT_SECRET=your_very_long_random_secret_key_minimum_32_characters
JWT_EXPIRES_IN=7d

# Anthropic Claude API
ANTHROPIC_API_KEY=sk-ant-api03-...

# Replicate (Stable Diffusion)
REPLICATE_API_TOKEN=r8_...

# Cloudinary
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=123456789012345
CLOUDINARY_API_SECRET=your_api_secret_here

# Twilio WhatsApp
TWILIO_ACCOUNT_SID=ACxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
TWILIO_AUTH_TOKEN=your_auth_token_here
TWILIO_WHATSAPP_NUMBER=whatsapp:+14155238886

# SendGrid Email
SENDGRID_API_KEY=SG.xxxxxxxxxxxxxxxxxxxx
SENDGRID_FROM_EMAIL=noreply@yourshowroom.com

# Frontend URL (for CORS)
FRONTEND_URL=http://localhost:3000
```

**Frontend** — create `frontend/.env.local`:

```env
NEXT_PUBLIC_API_URL=http://localhost:5000
```

### Running the App

**Start the backend server:**
```bash
cd backend
node scripts/seedAdmin.js    # Create first admin account
npm run dev                  # Start with nodemon (auto-restart)
```

**Start the frontend:**
```bash
cd frontend
npm run dev                  # Start Next.js dev server
```

**Open the app:**
```
Frontend:   http://localhost:3000
Admin:      http://localhost:3000/admin
Backend:    http://localhost:5000
```

**Login with default admin credentials:**
```
Email:    owner@showroom.com
Password: Admin@123
```
> ⚠️ Change these immediately after first login in `/admin/settings`

---

## 📁 Project Structure

```
tiles-vision-ai/
│
├── frontend/                        # Next.js 14 Application
│   ├── app/
│   │   ├── page.jsx                 # Landing page
│   │   ├── app/page.jsx             # Main visualizer
│   │   ├── catalogue/page.jsx       # Tile catalogue browser
│   │   ├── admin/
│   │   │   ├── page.jsx             # Admin dashboard
│   │   │   ├── tiles/page.jsx       # Tile manager
│   │   │   ├── leads/page.jsx       # Lead pipeline Kanban
│   │   │   ├── analytics/page.jsx   # Charts and reports
│   │   │   └── settings/page.jsx    # Showroom settings
│   │   └── auth/login/page.jsx
│   ├── components/
│   │   ├── visualizer/              # Core visualizer components
│   │   ├── catalogue/               # Catalogue UI components
│   │   ├── quotes/                  # Quote form + download gate
│   │   └── admin/                   # Admin panel components
│   ├── store/
│   │   ├── useVisualizerStore.js    # Zustand: app state
│   │   └── useAuthStore.js          # Zustand: admin auth
│   └── lib/
│       ├── api.js                   # Axios instance
│       └── utils.js                 # Helper functions
│
├── backend/                         # Node.js + Express API
│   ├── server.js                    # Entry point
│   ├── routes/                      # Route definitions
│   ├── controllers/                 # Business logic
│   ├── models/                      # Mongoose schemas
│   │   ├── Tile.model.js
│   │   ├── Visualization.model.js
│   │   ├── Lead.model.js
│   │   ├── User.model.js
│   │   └── Showroom.model.js
│   ├── services/
│   │   ├── ai.service.js            # Claude + Replicate
│   │   ├── cloudinary.service.js    # Image storage
│   │   ├── whatsapp.service.js      # Twilio messaging
│   │   ├── email.service.js         # SendGrid
│   │   ├── image.service.js         # Sharp processing
│   │   └── scheduler.service.js     # Cron automations
│   ├── middleware/
│   │   ├── auth.middleware.js       # JWT verification
│   │   ├── rateLimit.middleware.js
│   │   └── upload.middleware.js     # Multer config
│   ├── config/db.js                 # MongoDB connection
│   └── scripts/seedAdmin.js         # First admin setup
│
└── README.md
```

---

## 📡 API Reference

### Authentication
```
POST   /api/auth/login          Login admin → returns JWT token
POST   /api/auth/logout         Invalidate session
```

### Visualization (AI Core)
```
POST   /api/visualize/generate  Generate AI room from tile image + settings
POST   /api/visualize/upload    Apply tile to uploaded room photo
GET    /api/visualize/:id       Get visualization status + result
POST   /api/visualize/regen     Regenerate with same settings, new seed
```

### Tile Catalogue
```
GET    /api/tiles               List tiles (filter: finish, size, category, search)
GET    /api/tiles/:id           Get single tile
POST   /api/tiles               Add new tile (Admin)
POST   /api/tiles/bulk          Bulk import from CSV (Admin)
PATCH  /api/tiles/:id           Update tile (Admin)
DELETE /api/tiles/:id           Archive tile (Admin)
GET    /api/tiles/:id/qr        Get tile QR code PNG
```

### Leads & Quotes
```
POST   /api/quotes              Submit quote request (triggers WhatsApp)
GET    /api/quotes              List all leads (Admin)
GET    /api/quotes/:id          Get lead detail
PATCH  /api/quotes/:id/status   Update lead stage (Admin)
PATCH  /api/quotes/:id/note     Add internal note (Admin)
```

### Analytics
```
GET    /api/analytics/summary   Dashboard stat cards
GET    /api/analytics/daily     Daily visualization counts
GET    /api/analytics/top-tiles Top 10 tiles by views
GET    /api/analytics/funnel    Conversion funnel data
GET    /api/analytics/export    Download CSV/PDF report
```

### Share & Export
```
POST   /api/share/whatsapp      Send visualization via WhatsApp
GET    /api/share/link/:id      Generate 30-day shareable URL
GET    /api/download/:id        Download watermarked image
```

**Example Request — Generate Room:**
```bash
curl -X POST http://localhost:5000/api/visualize/generate \
  -H "Content-Type: application/json" \
  -d '{
    "tileImage": "data:image/jpeg;base64,...",
    "roomType": "living",
    "placement": "Full Room",
    "tileSize": "12x24",
    "finish": "Porcelain",
    "layout": "Herringbone",
    "customInstructions": "Warm Scandinavian lighting"
  }'
```

**Example Response:**
```json
{
  "success": true,
  "imageUrl": "https://res.cloudinary.com/your-cloud/generated/room-123.jpg",
  "sessionId": "sess_abc123xyz",
  "tags": ["12x24", "Porcelain", "Herringbone", "Full Room", "Living Room"],
  "prompt": "Ultra-realistic luxury living room interior..."
}
```

---

## 🌐 Deployment

### Backend → Railway

```bash
# 1. Push backend to GitHub
git push origin main

# 2. Connect Railway to your GitHub repo at railway.app
# 3. Add all environment variables in Railway → Settings → Variables
# 4. Railway auto-detects Node.js and deploys

# Ensure package.json has:
# "scripts": { "start": "node server.js" }
```

### Frontend → Vercel

```bash
# 1. Push frontend to GitHub
git push origin main

# 2. Connect Vercel to your GitHub repo at vercel.app
# 3. Add environment variables:
#    NEXT_PUBLIC_API_URL = https://your-app.railway.app
# 4. Vercel auto-detects Next.js and deploys
```

### Database → MongoDB Atlas

```bash
# 1. Create free M0 cluster at mongodb.com/cloud/atlas
# 2. Create database user
# 3. Whitelist Railway IP (or 0.0.0.0/0 for any IP)
# 4. Copy connection string to MONGODB_URI
```

| Service | Platform | Cost |
|---------|----------|------|
| Frontend | Vercel | Free |
| Backend | Railway | ~$5/mo |
| Database | MongoDB Atlas | Free (512MB) |
| Images | Cloudinary | Free (25GB) |
| AI Generation | Replicate | ~₹0.20/image |
| WhatsApp | Twilio | ~₹0.60/message |

---

## 📅 28-Day Build Roadmap

| Week | Focus | Status |
|------|-------|--------|
| **Week 1** (Days 1–7) | Node.js + Express + MongoDB + Auth System | 🔵 Foundation |
| **Week 2** (Days 8–14) | Claude AI + Replicate SDXL + Next.js Frontend | 🤖 AI Core |
| **Week 3** (Days 15–21) | Upload Mode + WhatsApp + Quotes + Catalogue | 📱 Features |
| **Week 4** (Days 22–28) | Admin Dashboard + Analytics + Deploy + Launch | 🚀 Ship It |

---

## 🗺️ Future Roadmap

- [ ] **AR Mobile Mode** — WebXR tile overlay on real floor using phone camera
- [ ] **AI Tile Recommender** — Claude analyzes room and recommends matching tiles
- [ ] **Room Measurement Tool** — auto-calculate tiles needed from drawn dimensions
- [ ] **Grout Color Selector** — choose grout color and preview in visualization
- [ ] **3D Room Walkthrough** — navigate a Three.js 3D scene with the selected tiles
- [ ] **Tile Comparison Mode** — view two tiles side-by-side in the same room
- [ ] **Gujarati / Hindi UI** — multilingual interface for regional showrooms
- [ ] **POS Integration** — won leads convert directly to Tally/Busy invoices
- [ ] **Multi-Showroom SaaS** — white-label platform for multiple showroom chains

---

## 🤝 Contributing

Contributions are welcome! Here's how to get started:

```bash
# 1. Fork the repository
# 2. Create your feature branch
git checkout -b feature/AmazingFeature

# 3. Make your changes and commit
git commit -m 'Add AmazingFeature'

# 4. Push to your branch
git push origin feature/AmazingFeature

# 5. Open a Pull Request
```

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code style and PR process.

**Areas where help is most needed:**
- 🧪 Writing tests (Jest for backend, Cypress for E2E)
- 🌍 Translations (Hindi, Gujarati, Marathi)
- 🎨 UI/UX improvements
- 📱 Mobile responsiveness fixes
- 🔌 New integrations (Zoho CRM, Tally, etc.)

---

## 🐛 Known Issues

- SAM segmentation may struggle with rooms that have complex patterns or low contrast floors
- Replicate API generation can take 20–40 seconds depending on server load
- Twilio WhatsApp sandbox requires recipients to opt-in before receiving messages

---

## 📄 License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for full details.

---

## 👤 Author

**Your Name**
- GitHub: [@yourusername](https://github.com/yourusername)
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/yourprofile)
- Email: your@email.com

---

## 🙏 Acknowledgements

- [Anthropic Claude](https://anthropic.com) — for the vision AI and prompt engineering backbone
- [Replicate](https://replicate.com) — for making Stable Diffusion accessible via API
- [Stability AI](https://stability.ai) — creators of Stable Diffusion XL
- [Meta AI Research](https://ai.meta.com) — for the Segment Anything Model (SAM)
- [Twilio](https://twilio.com) — for the WhatsApp Business API

---

<div align="center">

**If this project helped you, please give it a ⭐ on GitHub!**

Made with ❤️ for ceramic showrooms everywhere

</div>
