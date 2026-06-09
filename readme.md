# Compromised Website Tracker

A public dataset of websites compromised primarily for "cloaked gambling" 
SEO abuse, along with other compromise types including link injection, 
webshells, phishing, and malware delivery. Each entry represents a
compromised host or URL observed at a specific point in time.
Duplicate entries are generally avoided unless the compromise
type, payload, infrastructure, or observed behavior has materially changed.
Don't assume because you only see it months prior that it isn't still compromised.

## Purpose

This is my own little project that blew up to the point where I figured
I should put it here so it doesn't languish on my computer. This is not
meant to be fancy. I need to keep it simple so that I keep it up.

## What is cloaked gambling compromise?

Legitimate websites are hacked and injected with code that serves 
online gambling content (casino, slot, and betting sites) to search engine 
crawlers while showing the normal site to regular visitors. This manipulates 
search rankings for gambling keywords while evading detection.

## The Data

See `compromised-sites.csv`. Fields:
- `entry_id` — Sequential number
- `hostname` — Exact hostname observed in the compromised URL
- `url` — The compromised URL
- `urlscan_result` — Evidence link (urlscan.io scan)
- `date_found` — Date the compromise was observed and recorded (YYYY-MM-DD)
- `compromise_type` — Category of compromise
- `notes` — Observations about the specific compromise

## Compromise types:

- cloaked_gambling — Gambling content selectively shown to crawlers or specific visitors.
- gambling — Gambling content directly visible without cloaking.
- link_injection — Injected SEO spam or unauthorized outbound links.
- unauthorized_subdomain - Dangling subdomains and ones created explicitly for content unintended by the owners of the domain.
- open_directory — Exposed directory listing containing sensitive or unexpected content.
- phishing — Credential theft or impersonation content.
- malware — Malware distribution or malicious downloads.
- webshell — Presence of a remote administration or command execution script.
- c2_blockchain - Command & control via blockchain

## Data Quality

Entries are reviewed for duplicate domains before publication.
URLs are preserved as observed.
Evidence links are retained whenever possible through urlscan.io permalinks.

## Limitations

The presence of a site in this dataset indicates that a compromise was
observed at the listed date. It does not indicate when the compromise
began, whether it remains active, or the extent of the compromise.

## Scale

This dataset currently documents over 2,700 entries from February–June 2026, 
including sites from 80+ countries, government domains (.gov.bd, .gob.mx, 
.gov.ph, .gov.br, etc.), educational institutions, and small businesses.
The repository is currently being populated from a larger collection
and will continue to receive new entries as additional compromises are identified.

## Methodology

Sites are identified via urlscan.io scans using user agent spoofing, 
Google Rich Results testing, and DOM analysis. Evidence is preserved as 
urlscan.io permalinks.

## Reporting

If you own a listed site or are responsible for its administration,
please investigate and remediate the compromise if it remains present.

## Disclaimer

While every effort is made to verify compromises before inclusion, errors are possible.
Inclusion in this dataset should not be interpreted as evidence of negligence, intent, or current compromise status.

## License

Data is released under CC0 (public domain).
