"""
RSS Feed Registry — US Financial Markets
==========================================
Comprehensive, publicly available RSS feeds that update on a daily
(or intraday) basis. No API keys required for any of these.
 
Notes:
- URLs drift over time. Validate with a HEAD/GET request before
  production use (see validate_feeds() at bottom).
- Reuters discontinued public RSS in June 2020 — do not use
  feeds.reuters.com. A Google News workaround is included below.
- Bloomberg does not offer public RSS feeds at all.
- Some feeds (WSJ, Barron's, FT) surface headlines only; full
  articles sit behind a paywall.
"""
 
from typing import Dict, List
 
RSS_FEEDS: List[Dict[str, str]] = [
 
    # ------------------------------------------------------------------
    # 1. GENERAL MARKET / BUSINESS NEWS WIRES
    # ------------------------------------------------------------------
    {"category": "news", "name": "CNBC Markets", "url": "https://www.cnbc.com/id/15839135/device/rss/rss.html"},
    {"category": "news", "name": "CNBC Top News", "url": "https://www.cnbc.com/id/100003114/device/rss/rss.html"},
    {"category": "news", "name": "CNBC Finance", "url": "https://www.cnbc.com/id/10000664/device/rss/rss.html"},
    {"category": "news", "name": "CNBC Economy", "url": "https://www.cnbc.com/id/20910258/device/rss/rss.html"},
    {"category": "news", "name": "CNBC Earnings", "url": "https://www.cnbc.com/id/15839135/device/rss/rss.html"},
    {"category": "news", "name": "Yahoo Finance Top News", "url": "https://finance.yahoo.com/news/rssindex"},
    {"category": "news", "name": "MarketWatch Top Stories", "url": "http://feeds.marketwatch.com/marketwatch/topstories/"},
    {"category": "news", "name": "MarketWatch Real-Time Headlines", "url": "http://feeds.marketwatch.com/marketwatch/realtimeheadlines/"},
    {"category": "news", "name": "MarketWatch MarketPulse", "url": "http://feeds.marketwatch.com/marketwatch/marketpulse/"},
    {"category": "news", "name": "Investing.com General News", "url": "https://www.investing.com/rss/news.rss"},
    {"category": "news", "name": "Investing.com Stock Market News", "url": "https://www.investing.com/rss/stock_Stock-Market-News.rss"},
    {"category": "news", "name": "Investing.com Forex News", "url": "https://www.investing.com/rss/news_1.rss"},
    {"category": "news", "name": "Seeking Alpha - All News", "url": "https://seekingalpha.com/feed.xml"},
    {"category": "news", "name": "Seeking Alpha - Market Currents", "url": "https://seekingalpha.com/market_currents.xml"},
    {"category": "news", "name": "WSJ Markets", "url": "https://feeds.a.dj.com/rss/RSSMarketsMain.xml"},
    {"category": "news", "name": "WSJ US Business", "url": "https://feeds.a.dj.com/rss/WSJcomUSBusiness.xml"},
    {"category": "news", "name": "WSJ World News", "url": "https://feeds.a.dj.com/rss/RSSWorldNews.xml"},
    {"category": "news", "name": "Barron's", "url": "https://www.barrons.com/feed/rssnews"},
    {"category": "news", "name": "Financial Times - US", "url": "https://www.ft.com/rss/home/us"},
    {"category": "news", "name": "Business Insider Markets", "url": "https://markets.businessinsider.com/rss/news"},
    {"category": "news", "name": "Benzinga - All News", "url": "https://www.benzinga.com/feed"},
    {"category": "news", "name": "Motley Fool - Combined US", "url": "https://www.fool.com/feeds/index.aspx?feed_type=combined_us"},
    {"category": "news", "name": "Forbes Money", "url": "https://www.forbes.com/money/feed/"},
    {"category": "news", "name": "Fortune", "url": "https://fortune.com/feed"},
    {"category": "news", "name": "Zacks Investment Research", "url": "https://www.zacks.com/rss/rss_news_stock.php"},
    {"category": "news", "name": "Nasdaq - Original Content", "url": "https://www.nasdaq.com/feed/rssoutbound?category=Markets"},
    {"category": "news", "name": "Reuters (via Google News workaround)",
     "url": "https://news.google.com/rss/search?q=when:24h+allinurl:reuters.com/business&ceid=US:en&hl=en-US&gl=US",
     "note": "Reuters killed native RSS in 2020; this is a Google News query proxy"},
 
    # ------------------------------------------------------------------
    # 2. FEDERAL RESERVE / CENTRAL BANK
    # ------------------------------------------------------------------
    {"category": "fed", "name": "Federal Reserve - All Press Releases", "url": "https://www.federalreserve.gov/feeds/press_all.xml"},
    {"category": "fed", "name": "Federal Reserve - Monetary Policy (FOMC)", "url": "https://www.federalreserve.gov/feeds/press_monetary.xml"},
    {"category": "fed", "name": "Federal Reserve - Speeches", "url": "https://www.federalreserve.gov/feeds/speeches.xml"},
    {"category": "fed", "name": "Federal Reserve - Testimony", "url": "https://www.federalreserve.gov/feeds/testimony.xml"},
    {"category": "fed", "name": "Federal Reserve - Banking/Regulatory Press", "url": "https://www.federalreserve.gov/feeds/press_bcreg.xml"},
    {"category": "fed", "name": "Federal Reserve - H.15 Selected Interest Rates", "url": "https://www.federalreserve.gov/feeds/h15.xml"},
    {"category": "fed", "name": "Federal Reserve - Data Download Program (DDP)", "url": "https://www.federalreserve.gov/feeds/ddp.xml"},
    {"category": "fed", "name": "NY Fed - Press Releases", "url": "https://www.newyorkfed.org/rss/news.xml"},
    {"category": "fed", "name": "St. Louis Fed - FRED Blog", "url": "https://fredblog.stlouisfed.org/feed/"},
 
    # ------------------------------------------------------------------
    # 3. US TREASURY
    # ------------------------------------------------------------------
    {"category": "treasury", "name": "US Treasury - Press Releases", "url": "https://home.treasury.gov/rss/press-releases"},
    {"category": "treasury", "name": "US Treasury - Featured Stories", "url": "https://home.treasury.gov/rss/featured-stories"},
    {"category": "treasury", "name": "TreasuryDirect - News & Announcements", "url": "https://www.treasurydirect.gov/rss/news.xml"},
 
    # ------------------------------------------------------------------
    # 4. SEC / REGULATORY / EXCHANGES
    # ------------------------------------------------------------------
    {"category": "regulatory", "name": "SEC - Press Releases", "url": "https://www.sec.gov/news/pressreleases.rss"},
    {"category": "regulatory", "name": "SEC - Litigation Releases", "url": "https://www.sec.gov/rss/litigation/litreleases.xml"},
    {"category": "regulatory", "name": "SEC - Administrative Proceedings", "url": "https://www.sec.gov/rss/litigation/admin.xml"},
    {"category": "regulatory", "name": "SEC - Speeches & Statements", "url": "https://www.sec.gov/news/speeches-statements.rss"},
    {"category": "regulatory", "name": "SEC EDGAR - Latest Filings (all, customizable by form type/CIK)",
     "url": "https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&type=&dateb=&owner=include&count=100&output=atom",
     "note": "Append &company=, &CIK=, or &type=10-K/8-K etc. to scope to a ticker or filing type"},
    {"category": "regulatory", "name": "FINRA - News Releases", "url": "https://www.finra.org/rss.xml"},
    {"category": "regulatory", "name": "CFTC - Press Releases", "url": "https://www.cftc.gov/RSS/RSSGP/rssgp.xml"},
    {"category": "regulatory", "name": "FDIC - Press Releases", "url": "https://www.fdic.gov/news/rss/press-releases.xml"},
    {"category": "regulatory", "name": "Nasdaq - Press Releases", "url": "https://ir.nasdaq.com/rss/news-releases.xml"},
 
    # ------------------------------------------------------------------
    # 5. MACRO / ECONOMIC DATA RELEASE FEEDS
    # ------------------------------------------------------------------
    {"category": "macro", "name": "Bureau of Labor Statistics - All News Releases", "url": "https://www.bls.gov/feed/bls_latest.rss"},
    {"category": "macro", "name": "Bureau of Economic Analysis - News Releases", "url": "https://apps.bea.gov/rss/rss.xml"},
    {"category": "macro", "name": "US Census Bureau - Economic Indicators", "url": "https://www.census.gov/economic-indicators/rss.xml"},
    {"category": "macro", "name": "EIA - Today in Energy", "url": "https://www.eia.gov/rss/todayinenergy.xml"},
    {"category": "macro", "name": "EIA - Petroleum Status Report / Short-Term Outlook", "url": "https://www.eia.gov/rss/press_rss.xml"},
 
    # ------------------------------------------------------------------
    # 6. AGGREGATOR / DIY WORKAROUNDS (for sources with no native RSS)
    # ------------------------------------------------------------------
    {"category": "workaround", "name": "Google News - Custom Query Template",
     "url": "https://news.google.com/rss/search?q={QUERY}&ceid=US:en&hl=en-US&gl=US",
     "note": "Swap {QUERY} for e.g. 'when:24h+allinurl:bloomberg.com' to build a feed for any domain lacking native RSS"},
]
 
 
def validate_feeds(feeds: List[Dict[str, str]], timeout: int = 8) -> List[Dict[str, str]]:
    """
    Quick liveness check — flags dead/redirecting feeds before you
    wire them into a production ingestion job. Requires `requests`.
    """
    import requests
 
    results = []
    for feed in feeds:
        try:
            resp = requests.get(feed["url"], timeout=timeout, headers={"User-Agent": "Mozilla/5.0"})
            ok = resp.status_code == 200 and (
                "xml" in resp.headers.get("Content-Type", "") or resp.text.strip().startswith("<")
            )
            results.append({**feed, "status": resp.status_code, "live": ok})
        except Exception as e:
            results.append({**feed, "status": "error", "live": False, "error": str(e)})
    return results
 
 
if __name__ == "__main__":
    checked = validate_feeds(RSS_FEEDS)
    dead = [f for f in checked if not f["live"]]
    print(f"{len(RSS_FEEDS) - len(dead)}/{len(RSS_FEEDS)} feeds live")
    for f in dead:
        print(f"  DEAD: {f['name']} -> {f['url']}")