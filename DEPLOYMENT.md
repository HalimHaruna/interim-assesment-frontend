# Coinbase Clone - Deployment Guide

## 🚀 Deploying to Netlify

### Step 1: Build the Project

```bash
npm run build
```

### Step 2: Deploy to Netlify

Before publishing, set a neutral Netlify site name and avoid using "coinbase" in the domain.

Recommended format:

```text
yourname-crypto-app.netlify.app
```

#### Option A: Netlify CLI

1. Install Netlify CLI globally:

```bash
npm install -g netlify-cli
```

2. Login to Netlify:

```bash
netlify login
```

3. Deploy your site:

```bash
netlify deploy --prod
```

#### Option B: Netlify Dashboard

1. Go to [https://app.netlify.com](https://app.netlify.com)
2. Click "Add new site" > "Deploy manually"
3. Drag and drop your `dist` folder

#### Option C: Connect to GitHub

1. Push your code to GitHub
2. Go to [https://app.netlify.com](https://app.netlify.com)
3. Click "Add new site" > "Import an existing project"
4. Connect to your GitHub repository
5. Configure build settings:
   - **Build command**: `npm run build`
   - **Publish directory**: `dist`
6. Click "Deploy site"

### Step 3: Configure Redirects for React Router

Netlify needs a `_redirects` file to handle client-side routing properly.

Create a file at `public/_redirects` with:

```
/*    /index.html   200
```

Or add to your `netlify.toml`:

```toml
[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

## ✅ Checklist Before Deployment

- [ ] Netlify site name is neutral (no "coinbase" in domain)
- [ ] All pages render correctly
- [ ] Navigation works properly
- [ ] Links navigate correctly
- [ ] Responsive design works on mobile, tablet, and desktop
- [ ] No console errors
- [ ] Build completes successfully (`npm run build`)
- [ ] Test locally with `npm run preview` after building

## 📝 Environment Variables

For IA integration, configure environment variables for both frontend and backend.

Frontend (Netlify):

- `VITE_API_BASE_URL=https://your-backend-service-url/api`

Backend (Render):

- `PORT=5000`
- `MONGO_URI=your_mongodb_connection_string`
- `JWT_SECRET=your_strong_secret`
- `FRONTEND_URL=https://yourname-crypto-app.netlify.app`
- `NODE_ENV=production`

Netlify setup steps:

1. In Netlify Dashboard, go to Site settings > Build & deploy > Environment
2. Add your environment variables
3. Prefix frontend variables with `VITE_`

## ☁️ Deploy Backend (Render)

1. Push your repository to GitHub.
2. In Render, create a new **Web Service** and point it to this repository.
3. Set the root directory to `backend`.
4. Use build command:

```bash
npm install
```

5. Use start command:

```bash
npm run start
```

6. Add backend environment variables listed above.
7. Copy your Render backend URL and set `VITE_API_BASE_URL` in Netlify.

## 🔗 Custom Domain

To add a custom domain:

1. Go to your site in Netlify Dashboard
2. Navigate to "Domain settings"
3. Click "Add custom domain"
4. Follow Netlify's instructions to configure DNS

## 📊 Features Implemented

✅ React Router for client-side navigation
✅ Functional components with React hooks
✅ Reusable components (Button, Card, Input, etc.)
✅ Tailwind CSS v4 for styling
✅ Responsive design (mobile, tablet, desktop)
✅ React state management with useState
✅ Proper file structure and naming conventions
✅ Clean, readable code with comments

## 📁 Project Structure

```
src/
├── assets/          # Images, icons, and other static files
├── components/      # Reusable React components
│   ├── common/      # Shared components (Button, Card, Input)
│   ├── layout/      # Layout components (Navbar, Footer)
│   └── crypto/      # Crypto-specific components (CryptoCard, PriceChart)
├── pages/           # Page components
│   ├── Home.jsx
│   ├── Explore.jsx
│   ├── AssetDetail.jsx
│   ├── Learn.jsx
│   ├── SignIn.jsx
│   └── SignUp.jsx
├── data/            # Mock data and constants
├── hooks/           # Custom React hooks
├── App.jsx          # Main application with routing
├── App.css          # Global styles
├── main.jsx         # Application entry point
└── index.css        # Tailwind CSS imports
```

## 🎨 Pages Overview

1. **Home** (`/`) - Landing page with hero section, featured cryptocurrencies, and feature highlights
2. **Explore** (`/explore`) - Browse all cryptocurrencies with search and sorting
3. **Asset Detail** (`/asset/:id`) - Detailed view of a specific cryptocurrency
4. **Learn** (`/learn`) - Educational articles about crypto
5. **Sign In** (`/signin`) - User authentication page
6. **Sign Up** (`/signup`) - User registration page

## 🌐 Live Site

After deployment, your site will be available at:
`https://yourname-crypto-app.netlify.app`

## 💡 Tips

- Use Netlify's branch deploys to preview changes before going live
- Set up continuous deployment from GitHub for automatic updates
- Monitor your site's analytics in the Netlify Dashboard
- Check the deploy logs if you encounter any issues
- Verify backend and frontend URLs are live before submitting IA links
