# AgroVision Frontend — Space Data to Farm Decisions
**NASA Space Apps Challenge 2026 | Team Innovatrix | West Bengal, India**

## 1. Project Overview
**AgroVision** is a specialized agricultural decision-support platform designed for farmers, field workers, and researchers in West Bengal, India. It combines NASA Earth observation data (NASA POWER, GPM IMERG, SMAP, Landsat/HLS, MODIS) with local farming knowledge to evaluate climate risks, monitor in-season crop vitality, and plan sustainable annual crop rotations.

---

## 2. Technology Stack
- **Framework:** React 18.3+ (Functional Components & Hooks)
- **Bundler:** Vite 6.0+ (ES6+ Modules)
- **Routing:** React Router DOM 6.28+
- **Mapping:** Leaflet 1.9+ & React-Leaflet 4.2+ (OpenStreetMap tiles, zero paid keys)
- **Data Visualizations:** Recharts 2.13+
- **Iconography:** Lucide React
- **Design System:** Custom CSS variables based on the official AgroVision brand palette (Deep Navy, Satellite Blue, Agricultural Green, Lime Green, Electric Cyan).

---

## 3. Directory Structure
```
AgroVision/
├── frontend/
│   ├── public/
│   │   └── assets/
│   │       └── agrovision-logo.png     # Official uploaded emblem
│   ├── src/
│   │   ├── api/
│   │   │   └── apiClient.js            # Configurable fetch client (VITE_API_URL)
│   │   ├── components/
│   │   │   ├── common/                 # Navbar, Sidebar, Footer, Breadcrumbs, Badges
│   │   │   └── map/                    # FarmLocationPicker (Leaflet GPS & map pin)
│   │   ├── context/
│   │   │   └── FarmContext.jsx         # Global state (Active farm, demo profiles, units)
│   │   ├── data/                       # Mock data engine (Burdwan, Hooghly, Gosaba)
│   │   ├── layouts/                    # MainLayout (Public) & DashboardLayout
│   │   ├── pages/
│   │   │   ├── HomePage.jsx            # High-impact landing page (Before, During, After)
│   │   │   ├── AboutPage.jsx           # Vision, Team Innovatrix, scientific pledge
│   │   │   ├── NotFoundPage.jsx        # 404 handler
│   │   │   └── dashboard/
│   │   │       ├── OverviewPage.jsx    # Personalized farm status & 5 summary cards
│   │   │       ├── MyFarmsPage.jsx     # Farm profile cards & active toggling
│   │   │       ├── RegisterFarmPage.jsx# GPS & Leaflet registration + Bigha converter
│   │   │       ├── ClimatePage.jsx     # NASA POWER agroclimatology & 10-yr normals
│   │   │       ├── SatellitePage.jsx   # GPM rainfall, SMAP moisture, MODIS NDVI
│   │   │       ├── RiskPage.jsx        # Flood screening, coastal salinity, photo upload
│   │   │       ├── CropPlannerPage.jsx # 12-Month calendar & 2-3 rotation alternatives
│   │   │       ├── RecoveryPage.jsx    # Event timeline & harvest checklist
│   │   │       ├── ReportsPage.jsx     # Printable formal advisory sheet & CSV export
│   │   │       ├── ResearchPage.jsx    # NASA data provenance matrix & spatial specs
│   │   │       └── SettingsPage.jsx    # Bigha/Acre unit preference & language preview
│   │   ├── services/                   # Modular service layer ready for backend APIs
│   │   └── styles/                     # Variables, global resets, and component styles
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
├── backend/                            # Reserved for future Node.js / Express development
└── README.md
```

---

## 4. Development & Build Commands

Inside `AgroVision/frontend`:

```bash
# Install dependencies
npm install

# Start Vite development server (port 3000)
npm run dev

# Build for production
npm run build

# Preview production build locally
npm run preview
```

---

## 5. Demonstration Farm Profiles
The platform provides 3 selectable demonstration profiles representing key West Bengal agricultural zones:
1. **Purba Bardhaman Alluvial Plot:** Rice–Potato–Mustard/Sesame cropping. Explores groundwater conservation and pulse rotation to restore nitrogen.
2. **Singur, Hooghly Multi-Crop Farm:** Jute–Aman Paddy–Mustard cycle. Illustrates pest cycle breaks and organic carbon restoration via jute biomass.
3. **Gosaba, South 24 Parganas (Sundarbans):** Coastal saline lowland. Features tidal surge screening, post-monsoon soil salinity (EC > 4.0 dS/m), and zero-tillage relay grass pea (Khesari) adaptation.

---

## 6. Future Backend Integration (Node.js + Express)
To connect a live backend server:
1. Create a `.env` file in `AgroVision/frontend/`:
   ```env
   VITE_API_URL=http://localhost:5000
   ```
2. The `apiClient.js` service automatically routes requests to your backend endpoints:
   - `GET /api/health`
   - `GET /api/farms` & `POST /api/farms`
   - `GET /api/analyses/:id/climate`
   - `GET /api/analyses/:id/rotation`
   - `POST /api/analyses/:id/simulate`
3. Zero component changes are needed—the service layer automatically transitions from mock data to live server responses.
