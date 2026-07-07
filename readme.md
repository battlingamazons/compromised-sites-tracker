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
- cloaked_commerce - Commerce content selectively shown to crawlers or specific visitors.
- link_injection — Injected SEO spam or unauthorized outbound links.
- unauthorized_subdomain - Dangling subdomains and ones created explicitly for content unintended by the owners of the domain.
- open_directory — Exposed directory listing containing sensitive or unexpected content.
- phishing — Credential theft or impersonation content, including injected code that harvests site owner credentials.
- malware — Malware distribution or malicious downloads.
- webshell — Presence of a remote administration or command execution script.
- c2_blockchain - Command & control via blockchain

## Wallet / C2 tracking (added July 2026)

In addition to the main compromise log, this repo now includes two supplementary
files tracking cryptocurrency wallets tied to a recurring blockchain-based C2
scheme observed across many of the malware-flagged (`c2_blockchain|malware`)
entries in the main log:

- **`wallets.csv`** — the small, hand-maintained list of known operator/funding
  wallet addresses. As of this writing there are only a handful of these, and
  they appear to be reused heavily over long periods (likely over a year in at
  least one case), in contrast to the "resolver contract" addresses associated
  with each individual compromise, which appear to rotate frequently.
- **`wallet_sightings.csv`** — an append-only log of individual domains where a
  known wallet's associated smart contract was observed being called. Each row
  links a domain + date to a wallet address, the resolver contract used at that
  specific sighting, and (where available) a tria.ge detonation link.

### Design notes / limitations

- These files are linked to the main log by **domain name only**, not by row
  number or any other index. Row numbers in the main log shift as older
  entries are backfilled, so they are not a reliable key; domain names are
  stable and can be located with a simple search.
- `wallets.csv` records a `first_documented` date, which reflects the earliest
  sighting *recorded in this dataset* — not necessarily the wallet's actual
  first use. Reliable tracking of tria.ge detonation links only began around
  2026-04-26, and wallet identification before that point was inconsistent, so
  earlier activity by these same wallets almost certainly exists undocumented.
- Where a single detonation drops multiple malware stages with their own
  separate tria.ge sessions, `wallet_sightings.csv` includes only the primary
  detonation link (the one that reveals the resolver contract / wallet). The
  full set of related tria.ge sessions for a given finding remains documented
  in the main log's notes field for that entry, to avoid turning this file
  into another list-in-a-cell problem.
- No malware samples, loader scripts, or manifests (e.g. the `css.js`-style
  loaders used to reach these contracts) are included or will be included in
  this repo, even for older/historical findings. Only the on-chain addresses
  derived from analyzing that malware are published here.
- Resolver contract addresses are *not* treated as durable identifiers and are
  not deduplicated or tracked as their own entity — they are sighting-specific
  detail, kept alongside the wallet sighting for context.

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
including sites from 120+ countries, government domains (.gov.bd, .gob.mx, 
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
