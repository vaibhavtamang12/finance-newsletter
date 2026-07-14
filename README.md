# 📊 Finance Newsletter Pipeline

A fully automated, zero-cost daily finance newsletter system powered by Python, Gemini AI, and GitHub Actions.


## Financial News RSS Feed

- News wires (CNBC, MarketWatch, Investing.com, Seeking Alpha, WSJ, Benzinga) update continuously during market hours.
- Fed/Treasury/SEC feeds fire on an event basis (press releases, speeches, filings) — not a fixed daily cadence, but effectively daily in volume.
- BLS/BEA/Census feeds are the real backbone for macro release calendars (CPI, NFP, GDP revisions, PCE) — worth prioritizing since these move markets predictably on known dates.
- SEC EDGAR's "Latest Filings" feed is fully queryable — append &type=8-K or &CIK= to scope it to material events or specific tickers, which is probably more useful to you than the firehose.

Caveats:

- Bloomberg has no public RSS at all — you'd need their API or a scraping-adjacent workaround (not something I'd help build).
- WSJ/Barron's/FT feeds give headlines + snippets only; full text is paywalled.
- I included a validate_feeds() function in the file so you can run a liveness check before any of these go into a scheduled job — feed URLs shift without notice and you don't want a silent failure in a production ingestion pipeline.

## 🚀 Local Setup (Phase 1)
1. Clone or initialize the repository
2. `python -m venv .venv && source .venv/bin/activate`
3. `pip install -r requirements.txt`
4. `cp .env.example .env` and fill credentials
5. `git add . && git commit -m "init"`
6. Deploy via GitHub Actions (covered in later phases)

## 📂 Project Structure