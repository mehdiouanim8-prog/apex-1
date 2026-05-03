[README (2).md](https://github.com/user-attachments/files/27318414/README.2.md)
# 🤖 APEX-1 Mobile Trading Agent — Setup Guide

A real, AI-powered crypto trading agent that runs in your phone's browser, connects to your Binance account, and executes live trades.

---

## 📦 What's in the package

| File | Purpose |
|---|---|
| `index.html` | Main app UI |
| `app.js` | All trading logic + AI integration |
| `manifest.json` | Makes it installable as a phone app |
| `sw.js` | Offline support |
| `icon-192.png` / `icon-512.png` | App icons |

---

## ⚡ Quick Start (5 minutes)

### Step 1 — Host the files online
Your phone needs to load the app from a URL. Free options:

**Option A: Netlify Drop (easiest)**
1. Go to https://app.netlify.com/drop
2. Drag & drop the entire `apex-mobile` folder
3. Get a URL like `https://random-name.netlify.app`
4. Done! Open that URL on your phone.

**Option B: GitHub Pages**
1. Create a free GitHub account
2. Create a repo named `apex-1`
3. Upload all files
4. Settings → Pages → enable
5. Open `https://yourname.github.io/apex-1`

**Option C: Vercel**
1. Go to https://vercel.com → sign up (free)
2. New project → upload folder
3. Done — get a URL

### Step 2 — Install on phone
1. Open the URL in **Safari (iPhone)** or **Chrome (Android)**
2. Tap **Share → "Add to Home Screen"**
3. The APEX-1 icon now appears like a real app! 📱

### Step 3 — Get your API keys

**Binance API Keys:**
1. Log in to Binance.com → top right profile → **API Management**
2. Click **Create API** → **System Generated**
3. Name it: `APEX1-Mobile`
4. Set permissions:
   - ✅ **Enable Reading**
   - ✅ **Enable Spot & Margin Trading**
   - ❌ **DISABLE Withdrawals** (NEVER enable this!)
   - ❌ DISABLE Futures (unless you specifically want it)
5. Copy the **API Key** and **Secret Key**

**Anthropic API Key:**
1. Go to https://console.anthropic.com
2. Sign up / log in → **API Keys** → **Create Key**
3. Add ~$5 credit (enough for hundreds of analyses)
4. Copy the key (starts with `sk-ant-...`)

### Step 4 — Configure
1. Open APEX-1 on your phone
2. Tap the ⚙ settings icon (top right)
3. Paste all 3 API keys
4. Adjust risk settings:
   - **Max % per trade**: 10–20% recommended
   - **Stop-loss %**: 5–8% recommended
   - **Take-profit %**: 10–15% recommended
   - **Auto-trade interval**: 30 minutes (or longer for less frequent trading)
5. Tap **SAVE**

### Step 5 — Start trading!
- Tap **⚡ RUN AI ANALYSIS** to get AI signals manually
- Tap **▶ AUTO-START** at the bottom to let the bot run on its own
- Watch trades appear in the Portfolio and Log tabs

---

## 🎯 How it works

```
┌───────────────────────────────────────────────┐
│  Phone PWA (your dashboard)                   │
└─────────┬─────────────────────────┬───────────┘
          │                         │
          ▼                         ▼
   ┌──────────────┐         ┌──────────────────┐
   │  BINANCE API │         │  CLAUDE AI API   │
   │  - Live data │         │  - Web search    │
   │  - Place     │         │  - Analyze data  │
   │    orders    │         │  - Make signals  │
   │  - Account   │         │  - Review trades │
   └──────────────┘         └──────────────────┘
```

1. **Every 15 sec**: Phone fetches live Binance prices
2. **When triggered**: Sends market data + your portfolio + past trades to Claude AI
3. **Claude searches the web** for breaking news and sentiment
4. **AI returns signals** with entry/target/stop levels
5. **Auto-mode** executes trades; **manual mode** asks you first
6. **Stop-loss & take-profit** auto-close losing/winning trades

---

## 🔒 Security

- ✅ Your API keys are stored **ONLY on your phone** (browser local storage)
- ✅ Keys are sent **directly to Binance/Anthropic** — never to my server (there is no server)
- ✅ The app is just static files — no backend
- ⚠️ NEVER share your phone with someone if APEX-1 is set up
- ⚠️ If you lose your phone, **immediately delete the API key on Binance.com**

---

## ⚠️ Critical Risk Warnings

1. **Crypto can lose 50%+ in days.** AI is not magic.
2. **Start with $50–$100** until you've watched the bot for at least a week.
3. **Auto-trading is risky** — bugs, network issues, or API outages can cause losses.
4. **The "self-review" feature** lets the AI read its past trades, but it doesn't truly "learn." Each session is independent.
5. **Stop-loss is your safety net** — never disable it.
6. **Tax**: In Morocco, crypto gains may be taxable. Keep records.

---

## 🛠 Troubleshooting

| Problem | Fix |
|---|---|
| "Binance API keys not set" | Open ⚙ → paste keys → save |
| "Invalid API key" | Re-copy from Binance, no spaces |
| "Insufficient balance" | Deposit USDT to your Binance Spot wallet |
| "AI: 401 error" | Check Anthropic key + that you have credits |
| App doesn't update | Pull down to refresh, or close & reopen |
| Trades fail | Check Binance permissions enabled "Spot Trading" |

---

## 🎨 Customization

Edit `app.js` to change:
- `COINS` — which crypto pairs to trade
- AI prompt (in `runAIAnalysis()`) — change the trading strategy
- Refresh intervals at the bottom of `init()`

---

## 💬 Final advice from APEX-1's creator

This bot is a tool, not a money-printer. The market is brutal and unpredictable. Even pros lose. Use small amounts, watch carefully, and turn it off if you see losses mounting. AI signals are educated guesses — never bet money you can't lose.

Now go make some trades. Good luck. 🚀
