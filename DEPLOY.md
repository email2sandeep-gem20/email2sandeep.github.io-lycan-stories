# Lycan Lore — Deployment Guide

## Free Hosting Options (No Payment Required)

### Option 1: GitHub Pages (Recommended — Free Forever)
1. Create a free account at github.com
2. Click "New Repository" → name it `lycan-lore`
3. Upload `index.html` to the repo
4. Go to Settings → Pages → Source: "main branch"
5. Your site is live at: `https://yourusername.github.io/lycan-lore`

### Option 2: Netlify (Free tier, drag-and-drop)
1. Create a free account at netlify.com
2. Go to "Sites" → Drag and drop the `index.html` file
3. Netlify gives you a free URL instantly: `https://random-name.netlify.app`
4. You can add a custom domain (e.g. lycanlore.org) in settings

### Option 3: Vercel (Free tier)
1. Create a free account at vercel.com
2. Import from GitHub or drag-and-drop
3. Live at: `https://lycan-lore.vercel.app`

---

## Adding Real Login (Free Options)

### Firebase Authentication (Google's free auth)
1. Go to console.firebase.google.com
2. Create a project → Authentication → Sign-in Methods → Enable Email/Password + Google
3. Add this to `<head>`:
```html
<script src="https://www.gstatic.com/firebasejs/10.0.0/firebase-app.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.0.0/firebase-auth.js"></script>
```
4. Replace the `handleAuth()` and `handleGoogleAuth()` functions with Firebase SDK calls

### Supabase (Free PostgreSQL + Auth)
1. supabase.com → New Project (free tier: 500MB, 50k monthly active users)
2. Authentication is built-in with magic links, Google OAuth, etc.
3. Also stores user data, story saves, donation records

---

## Adding Real Payments

### Stripe (Recommended for international)
1. Create account at stripe.com (free to set up, 2.9% + 30¢ per transaction)
2. Create a "Payment Link" or "Donation Link" in the Stripe Dashboard
3. Replace the `handleDonation()` alert with:
```javascript
window.location.href = 'https://buy.stripe.com/YOUR_PAYMENT_LINK';
```
4. For dynamic amounts, use Stripe Checkout API

### Razorpay (Best for India / UPI)
1. Create account at razorpay.com (free, 2% per transaction)
2. Add the Razorpay script and replace `handleDonation()`:
```html
<script src="https://checkout.razorpay.com/v1/checkout.js"></script>
```
3. Create a Razorpay Payment Link for fixed amounts, or use the JS SDK for dynamic

### PayPal Donate Button
1. paypal.com/donate/buttons
2. Generate a donate button with your PayPal email
3. Replace the support button href with your PayPal donation link

---

## Custom Domain
- Buy `lycanlore.org` from Namecheap (~$12/year) or Google Domains
- Point DNS to your Netlify/Vercel/GitHub Pages host
- Free SSL certificate is included automatically

---

## CMS for Non-Technical Story Updates

### Forestry / TinaCMS (Free)
- Lets you edit stories through a visual CMS without touching code
- Connect to your GitHub repo for automatic deployments

### Notion as CMS
- Write stories in Notion, use the Notion API to fetch content
- Free for small teams

---

## What's Already Built In
- ✅ Full homepage with all sections
- ✅ Login/Register modal (ready to connect to Firebase or Supabase)
- ✅ Google OAuth button (ready to wire up)
- ✅ Story reader modals with 6 full stories
- ✅ Donation/support modal with amount selection
- ✅ Payment provider instructions (Stripe, Razorpay, PayPal)
- ✅ Themes section (9 themes)
- ✅ Scrolling ticker, investor CTA, footer
- ✅ Fully mobile responsive
- ✅ No dependencies — single HTML file, works anywhere
