# Base-Profit-Calculator
## 🚀 Build & Launch an Advanced Crypto Profit Calculator on Base (Using v0)

- Investment: $0
- Experience Required: Beginner-friendly
- Time Required: ~10–15 Minutes

- This guide shows you how to build and deploy a modern Crypto Profit & Risk Calculator as a Base Mini App using v0 and Farcaster.

- We are not building a basic calculator.

- We are building a trader-focused tool with:

- Gross Profit calculation

- Net Profit (after fees & slippage)

- ROI %

- Break-even price

- Optional Stop Loss

- Risk / Reward ratio

- Modern dark UI

## 🛠 Required Accounts & Tools

Create accounts:

- v0
`https://v0.app/ref/R27EJH`

- Farcaster
`https://farcaster.xyz/~/code/2A298U`

- Base App
`https://base.app/invite/friends/HJRWZTSG`

⚠ Important: Connect your Farcaster account inside the Base App.

### ✅ STEP 1 — Generate the Crypto Profit Calculator (Using v0)

- Go to v0 and paste this prompt:

```Create a modern dark-themed crypto profit calculator using Next.js and Tailwind CSS.

Inputs:
- Buy price
- Sell price
- Token amount
- Trading fee (%)
- Slippage (%)
- Optional Stop Loss price

Outputs (calculated in real-time):
- Gross profit
- Net profit (after fees and slippage)
- ROI percentage
- Break-even price
- Risk/Reward ratio (if stop loss provided)

Use React useState.
Make results update instantly.
Highlight profit in green and loss in red.
Use glassmorphism card design.
Make it responsive and clean.


Core Calculation Logic (Reference)

Gross Profit:

(Sell Price - Buy Price) × Amount


Total Fees:

(Buy Price × Amount × Fee%) + (Sell Price × Amount × Fee%)


Slippage Cost:

Sell Price × Amount × Slippage%


Net Profit:

Gross Profit - Total Fees - Slippage Cost


ROI %:

(Net Profit / (Buy Price × Amount)) × 100


Break-even Price:

(Buy Price × Amount + Total Fees) ÷ Amount


Risk/Reward Ratio:

(Take Profit - Entry) ÷ (Entry - Stop Loss)
```
- v0 will generate:
```
/components/profit-calculator.tsx
/app/page.tsx
Tailwind styling
Full calculation logic
```

### ✅ STEP 2 — Deploy the Project

- Inside v0:

- Click Deploy

- After deployment:

- Copy your live URL.

Example:

``https://your-project.vercel.app``


Save it — you will reuse it multiple times.

### ✅ STEP 3 — Create the Farcaster Manifest File

Inside your project, create:

```/public/.well-known/farcaster.json```

- Before Pasteing this, paste your `Project name` & `Project URL`

Paste:
```
{
  "accountAssociation": {
    "header": "",
    "payload": "",
    "signature": ""
  },
  "miniapp": {
    "version": "1",
    "name": "Crypto Profit Calculator",
    "subtitle": "Calculate ROI & Risk Instantly",
    "description": "Advanced crypto profit calculator with fee, slippage and risk management tools",
    "homeUrl": "https://your-domain.com",
    "iconUrl": "https://your-domain.com/icon.png",
    "splashImageUrl": "https://your-domain.com/splash.png",
    "splashBackgroundColor": "#0f172a",
    "screenshotUrls": [
      "https://your-domain.com/screenshot.png"
    ],
    "primaryCategory": "finance",
    "tags": ["crypto", "trading", "roi", "utility"],
    "tagline": "Calculate Before You Trade",
    "heroImageUrl": "https://your-domain.com/screenshot.png",
    "ogTitle": "Crypto Profit Calculator",
    "ogDescription": "Estimate profit, ROI and risk before entering a trade",
    "ogImageUrl": "https://your-domain.com/screenshot.png",
    "noindex": false
  }
}

```
Replace:

`https://your-domain.com`


With your deployed URL.

### ✅ STEP 4 — Add Required Images

- Inside /public add:

- icon.png → 300×300

- splash.png → 200×200

- screenshot.png → 1284×2778
  
- OR use this Prompt
  ```
  I am attaching this image adjust it's size and resolution as required icon.png → 300×300, splash.png → 200×200, screenshot.png → 1284×2778, and use it in our mini app for all these forms
  ```
Use your app screenshot. Keep dark theme consistency.

### ✅ STEP 5 — Add Mini App Embed Metadata

- In /app/layout.tsx, inside metadata:
```
other: {
  "fc:miniapp": JSON.stringify({
    version: "1",
    imageUrl: "https://your-domain.com/screenshot.png",
    button: {
      title: "Open Calculator",
      action: {
        type: "launch_frame",
        name: "Crypto Profit Calculator",
        url: "https://your-domain.com",
        splashImageUrl: "https://your-domain.com/splash.png",
        splashBackgroundColor: "#0f172a"
      }
    }
  })
}

```
This enables:

Embed preview

Launch button

Splash screen

### ✅ STEP 6 — Add Farcaster Mini App SDK

- Install:
```
npm install @farcaster/miniapp-sdk
```

- In /app/page.tsx:
```
import { useEffect } from "react";
import sdk from "@farcaster/miniapp-sdk";

useEffect(() => {
  sdk.actions.ready();
}, []);
```

Without sdk.actions.ready(), your splash screen will not close.

### ✅ STEP 7 — Update Next.js Config

- Update /next.config.mjs:
```
const nextConfig = {
  turbopack: {},
};

export default nextConfig;
```

Remove old webpack configs if present.

### ✅ STEP 8 — Verify in Farcaster Developer Mode

- Open Farcaster (Desktop)

- Enable Developer Mode

- Go to Mini App Manifest Tools

- Paste your deployed URL

- Click Fetch

- Click Generate Account Association

- Scan QR Code

- Copy:
```
header
payload
signature
```
- Paste them into your farcaster.json.

- Re-deploy.

- Re-verify.

- Submit.

### ✅ STEP 9 — Connect & Publish on Base

- Download Base App

- Login

- Connect the same Farcaster account

- Visit https://base.dev

- Submit your Mini App
