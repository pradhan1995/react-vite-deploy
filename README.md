# 🛒 DNS — Daily Need Store

> **The Super Grocery Store** — Quick-commerce style React + TypeScript frontend for a local Indian kiryana/general store.

---

## ✨ Features

- **Product Catalog** — Grid with category filter pills, search, add-to-cart with quantity stepper, floating cart FAB
- **Product Detail** — Full info + related products from same category
- **Cart** — Item management, delivery fee calculation, order summary
- **Checkout** — Delivery vs pickup toggle, customer form, live total
- **OTP Verification** — 6-digit auto-focus inputs, resend with 30s cooldown
- **Order Tracking** — Visual status timeline, pay-now button, shipping info, confetti on delivery 🎉
- **Hindi/English toggle** — Full i18n with translations object
- **Dark glassmorphism UI** — Purple (#7C6FE9) accent, green (#34D399) success
- **Mobile-first** — 2-col grid on mobile, up to 5-col on desktop
- **Zustand** — Cart + language state with localStorage persistence
- **Lazy routes** — Code-split pages via React.lazy + Suspense

---

## 🚀 Quick Start

```bash
# 1. Install dependencies
npm install

# 2. Set your API URL (or leave blank to use mock data)
echo "VITE_API_URL=http://localhost:8000" > .env

# 3. Run dev server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000)

---

## 📁 Project Structure

```
src/
├── api/
│   └── index.ts          # API layer + mock data fallback
├── components/
│   ├── layout/
│   │   ├── Navbar.tsx
│   │   ├── Navbar.module.css
│   │   ├── FloatingCartButton.tsx
│   │   └── FloatingCartButton.module.css
│   ├── ui/
│   │   ├── Button.tsx / .module.css
│   │   ├── Badge.tsx / .module.css
│   │   ├── Spinner.tsx / .module.css
│   │   ├── QuantityStepper.tsx / .module.css
│   │   └── EmptyState.tsx / .module.css
│   ├── CategoryPills.tsx / .module.css
│   └── ProductCard.tsx / .module.css
├── hooks/
│   └── useT.ts           # useT() translation hook + useAsync()
├── i18n/
│   └── translations.ts   # EN + HI strings
├── pages/
│   ├── CatalogPage.tsx / .module.css
│   ├── ProductDetailPage.tsx / .module.css
│   ├── CartPage.tsx / .module.css
│   ├── CheckoutPage.tsx / .module.css
│   ├── OtpPage.tsx / .module.css
│   └── TrackingPage.tsx / .module.css
├── store/
│   ├── cartStore.ts       # Zustand cart with localStorage
│   └── langStore.ts       # Zustand lang toggle + order state
├── types/
│   └── index.ts           # All TypeScript types
├── utils/
│   ├── confetti.ts        # Confetti on delivery
│   └── format.ts          # Currency, date formatters
├── App.tsx                # Lazy routes + BrowserRouter
├── main.tsx
└── index.css              # CSS custom properties + global styles
```

---

## 🔌 API Endpoints

| Method | Endpoint              | Description              |
|--------|-----------------------|--------------------------|
| GET    | `/api/catalog`        | All products             |
| GET    | `/api/catalog/:id`    | Product + related        |
| POST   | `/api/order`          | Place order → returns orderRef |
| POST   | `/api/order/verify`   | Verify OTP               |
| POST   | `/api/order/resend-otp` | Resend OTP             |
| GET    | `/api/track/:ref`     | Order tracking info      |

### Mock Mode
If `VITE_API_URL` is empty, the app uses **built-in mock data** with 18 products and simulated API responses. OTP `000000` will trigger an error; any other 6-digit code succeeds.

---

## 🎨 Design System

| Token | Value |
|-------|-------|
| `--purple` | `#7C6FE9` — Primary accent |
| `--green` | `#34D399` — Success / in-stock |
| `--bg` | `#0d0d14` — Page background |
| `--font-display` | Syne — Headings |
| `--font-body` | DM Sans — Body |

---

## 🛠 Tech Stack

- **React 18** + **TypeScript**
- **Vite 5** — Build tool
- **React Router v6** — Lazy-loaded routes
- **Zustand 4** — State management with persistence
- **CSS Modules** — Scoped styles
- **canvas-confetti** — Delivery celebration
- **clsx** — Conditional class names

---

## 📦 Build for Production

```bash
npm run build
npm run preview
```

Output goes to `dist/` — deploy to any static host (Vercel, Netlify, etc).
