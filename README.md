# MDA Stock Investing Club — Simulator

Founded by **Jack & Joseph Mizrachi**

A stock investment simulator with **real-time prices from Yahoo Finance**, short selling, options trading, AI analysis, and a leaderboard.

## Features

- **Real prices** — Every price comes from Yahoo Finance via server-side API proxy (no CORS issues)
- **46+ stocks** — AAPL, MSFT, NVDA, TSLA, META, GOOGL, AMZN, JPM, and many more
- **Search any ticker** — Type any stock symbol to find and trade it
- **Auto-refresh** — Prices update every 10 seconds
- **Short selling** — Short stocks with 50% margin requirement
- **Options** — Buy calls and puts with strike price and expiration
- **AI Analysis** — Built-in stock recommendations (Strong Buy → Strong Sell)
- **Portfolio tracking** — P&L, holdings with live prices, trade history
- **Leaderboard** — Compete with other members
- **TradingView charts** — Interactive second-by-second charts
- **$5,000 starting capital**

## Deploy to Vercel (Free — 2 minutes)

### Option 1: One-Click Deploy

1. Push this folder to a GitHub repository
2. Go to [vercel.com](https://vercel.com)
3. Click **"New Project"**
4. Import your GitHub repo
5. Click **Deploy** — that's it!

### Option 2: Vercel CLI

```bash
npm install -g vercel
cd mda-site
vercel
```

Follow the prompts. Your site will be live at `https://your-project.vercel.app`

### Option 3: Run Locally

```bash
cd mda-site
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000)

## Project Structure

```
mda-site/
├── pages/
│   ├── index.js          # Main app (all UI + trading logic)
│   ├── _app.js           # Next.js wrapper
│   └── api/
│       ├── quotes.js     # Yahoo Finance price proxy
│       └── search.js     # Stock ticker search
├── styles/
│   └── globals.css       # Global styles
├── package.json
├── next.config.js
└── README.md
```

## How Prices Work

The app fetches stock quotes from Yahoo Finance through a Next.js API route (`/api/quotes`). This runs server-side on Vercel, so there are no CORS issues. Prices refresh every 10 seconds automatically. When you open a trade, it fetches the latest price for that specific stock.

**No API key required** — Yahoo Finance's public quote endpoint is used.

## Adding a Shared Leaderboard (Optional)

The leaderboard currently uses `localStorage` (per-browser). To make it shared across all users:

1. Create a free [Supabase](https://supabase.com) or [Firebase](https://firebase.google.com) project
2. Create a `leaderboard` table with columns: `username`, `email`, `totalValue`, `pnl`, `pnlPercent`, `trades`
3. Replace the `localStorage` calls in `index.js` with your database client

## Tech Stack

- **Next.js 14** — React framework with API routes
- **Yahoo Finance** — Real-time stock data (no API key needed)
- **TradingView** — Interactive chart widgets
- **Vercel** — Free hosting with serverless functions

## License

Built for MDA Stock Investing Club. Educational use only. Not financial advice.
