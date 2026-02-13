# Base-Calculator

## 🚀 How to Build & Launch Your Base Mini App (Using v0)

Investment: $0

Experience Required: None

Time Required: ~10 Minutes

🛠 Required Accounts & Tools

- Create a v0 account
`https://v0.app/ref/R27EJH`

- Create a Farcaster account
`https://farcaster.xyz/~/code/2A298U`

- Create a Base App account
`https://base.app/invite/ethicalearn/HBB3DT78`

⚠ Important: Connect your Farcaster account inside the Base App.

### ✅ STEP 1 — Create the Calculator App (Using v0)

Go to v0 and prompt:
```
Create a modern dark theme calculator app using Next.js and Tailwind CSS. Include add, subtract, multiply and divide operations. Use React useState. Make it responsive and clean.
```
v0 will generate:
```
/components/calculator.tsx

/app/page.tsx

Tailwind styling

Full calculator logic
````
You do NOT need to manually code everything.

### ✅ STEP 2 — Deploy the Project

- Click Deploy inside v0.

Once deployed:

 - Copy your live URL

Save it (you’ll need it multiple times)

Example:

`https://your-project.vercel.app`

### ✅ STEP 3 — Create the Farcaster Manifest File

- Inside your project, create this file:
```
/public/.well-known/farcaster.json
```
- My project name : 
  My url link : 

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
    "name": "Your Project Name",
    "subtitle": "Fast & Easy Math",
    "description": "A simple calculator for basic arithmetic operations",
    "homeUrl": "https://your-domain.com",
    "iconUrl": "https://your-domain.com/icon.png",
    "splashImageUrl": "https://your-domain.com/splash.png",
    "splashBackgroundColor": "#1a1a1a",
    "screenshotUrls": [
      "https://your-domain.com/screenshot.png"
    ],
    "primaryCategory": "utility",
    "tags": ["calculator", "math", "utility"],
    "tagline": "Calculate Instantly",
    "heroImageUrl": "https://your-domain.com/screenshot.png",
    "ogTitle": "Calculator",
    "ogDescription": "A simple calculator for basic math",
    "ogImageUrl": "https://your-domain.com/screenshot.png",
    "noindex": false
  }
}
```

Replace:

`https://your-domain.com`


with your deployed URL.

### ✅ STEP 4 — Add Required Images

- Inside /public add:

• icon.png → 300×300

• splash.png → 200×200

• screenshot.png → 1284×2778

- You can:

Use your app screenshot

Resize with any online image tool

Keep dark theme for consistency

### ✅ STEP 5 — Add Mini App Embed Metadata
```
In /app/layout.tsx, add this inside metadata:

other: {
  "fc:miniapp": JSON.stringify({
    version: "1",
    imageUrl: "https://your-domain.com/screenshot.png",
    button: {
      title: "Open Calculator",
      action: {
        type: "launch_frame",
        name: "Calculator",
        url: "https://your-domain.com",
        splashImageUrl: "https://your-domain.com/splash.png",
        splashBackgroundColor: "#1a1a1a"
      }
    }
  })
}

```
This enables:

Embed preview

Launch button

Splash screen config

✅ STEP 6 — Add Farcaster Mini App SDK

Install:
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

⚠ This is CRITICAL.
Without sdk.actions.ready(), your splash screen won’t close.

### ✅ STEP 7 — Update Next.js Config

- Update /next.config.mjs:
```
const nextConfig = {
  turbopack: {},
};

export default nextConfig;
```

- Remove old webpack configs if present.

### ✅ STEP 8 — Verify in Farcaster Developer Mode

- Open Farcaster on Desktop

- Enable Developer Mode

- Go to Mini App Manifest Tools

- Paste your deployed URL

- Click Fetch

- Click Generate Account Association

- Scan QR code

- Verify

- Copy the generated:
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

- Login with email

- Connect same Farcaster account
```
Visit: https://base.dev
```
- Sign in

- Submit your Mini App

#### Later we will make more complex apps so stay tuned🚀🚀
