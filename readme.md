# Compromised Website Tracker

A public dataset of websites compromised primarily for "cloaked gambling" 
SEO abuse, along with other compromise types including link injection, 
webshells, phishing, and malware delivery. Each entry represents a
compromised host or URL observed at a specific point in time.
Duplicate entries are generally avoided unless the compromise
type, payload, infrastructure, or observed behavior has materially changed.
Don't assume because you see it months prior that it isn't still compromised.

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
- `date_found` — Date the compromise was observed and recorded (YYYY-MM-DD)
- `compromise_type` — Category of compromise
- `notes` — Observations about the specific compromise

## Compromise types:

- cloaked_gambling — Gambling content selectively shown to crawlers or specific visitors.
- gambling — Gambling content directly visible without cloaking.
- link_injection — Injected SEO spam or unauthorized outbound links.
- open_directory — Exposed directory listing containing sensitive or unexpected content.
- phishing — Credential theft or impersonation content.
- malware — Malware distribution or malicious downloads.
- webshell — Presence of a remote administration or command execution script.

## Scale

This dataset currently documents over 2,700 entries from February–June 2026, 
including sites from 80+ countries, government domains (.gov.bd, .gob.mx, 
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
