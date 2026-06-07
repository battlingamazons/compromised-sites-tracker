# Compromised Website Tracker

A public dataset of websites compromised primarily for "cloaked gambling" 
SEO abuse, along with other compromise types including link injection, 
webshells, phishing, and malware delivery.

## What is cloaked gambling compromise?

Legitimate websites are hacked and injected with code that serves Turkish 
online gambling content (casino, slot, and betting sites) to search engine 
crawlers while showing the normal site to regular visitors. This manipulates 
search rankings for gambling keywords while evading detection.

## The Data

See `data/compromised-sites.csv`. Fields:
- `entry_id` — Sequential number
- `url` — The compromised URL
- `urlscan_result` — Evidence link (urlscan.io scan)
- `date_found` — When documented (YYYY-MM-DD)
- `compromise_type` — Category of compromise
- `notes` — Observations about the specific compromise

## Scale

This dataset currently documents over 2,700 entries from February–June 2026, 
including sites from 80+ countries, government domains (.gov.bd, .gov.mx, 
.gov.ph, .gov.br, etc.), educational institutions, and small businesses.
I am just starting to put this into here. I will also be adding new entries.

## Methodology

Sites are identified via urlscan.io scans using Googlebot user agent spoofing, 
Google Rich Results testing, and DOM analysis. Evidence is preserved as 
urlscan.io permalinks.

## Reporting

If you own a site listed here or have access to the levers of power to do
something about these compromises, then please do--espeicaly the government
and educational ones.

## License

Data is released under CC0 (public domain).
