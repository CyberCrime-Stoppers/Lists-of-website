
---

## 📋 Platform Overview

| Attribute | Details |
|-----------|---------|
| **Founded** | December 2022 (launched Dec 5, 2022) |
| **Headquarters** | Melbourne, Victoria, Australia |
| **Operating Company** | Kick Streaming Pty Ltd |
| **Parent Company** | Easygo Entertainment Pty Ltd |
| **Owners** | Ed Craven & Bijan Tehrani (Stake.com co-founders) |
| **Users** | ~100 million total users (early 2026) |
| **Hours Watched** | 4.5 billion hours (2025), 500+ million (March 2026) |

---

## 🔐 Ownership & Corporate Structure

```
Ed Craven + Bijan Tehrani (Melbourne billionaires)
        ↓
Ashwood Holdings Pty Ltd (Craven's vehicle) + Tehrani personally (50% each)
        ↓
Easygo Entertainment Pty Ltd (parent company)
        ↓
Kick Streaming Pty Ltd (operating entity)
```

**Key facts:**
- Kick has **never raised outside capital** — entirely self-funded by the owners
- Bijan Tehrani confirmed **~$1 billion personal investment** into Kick by April 2026
- Same parent company as **Stake.com** (crypto gambling platform)
- Not BBB accredited (registered agent in Delaware, but Australian-based)

---

## 💰 Creator Economics

- **Revenue split: 95/5** (creator keeps 95% of subscription revenue — drastically better than Twitch's 50/50)
- **No ads on platform** according to their terms
- High-profile exclusive deals signed (xQc $100M non-exclusive, Adin Ross, Amouranth, Trainwreckstv)
- Creator-first positioning with "authentic engagement" algorithm rollout (April 2026, 10% of users)

---

## ⚠️ Security & Privacy Considerations (for your cybersec context)

Given your background in security hardening and anti-telemetry practices, here are notable flags:

| Concern | Details |
|---------|---------|
| **Gambling ties** | Primary funding source is Stake.com crypto casino — raises questions about profit motives and content moderation |
| **Moderation stance** | Looser moderation compared to Twitch, specifically allowing gambling content banned elsewhere |
| **Data jurisdiction** | Australian company (Five Eyes intelligence alliance member) |
| **Terms of service** | Broad rights granted to platform over user accounts/data; "Company has absolute right to manage, regulate, control, modify or eliminate" |
| **Trackers/analytics** | Standard streaming platform analytics; no public disclosure of third-party SDK integrations |
| **No independent audit** | No transparency reports or third-party security audits published |

---

## 🌐 Domain Information

- **Primary domain:** `kick.com`
- **App availability:** iOS, Android, web browser
- **Wildcards expected:** `*.kick.com`, API endpoints likely `*.api.kick.com`
- **No public threat intel reports** as of 2026, but gambling-related infrastructure often attracts adversarial interest

---

## 🎯 Who Should Use Kick?

| Good fit | May not be ideal |
|----------|------------------|
| Streamers wanting higher revenue share | Privacy purists concerned about Five Eyes jurisdiction |
| Gambling-adjacent content creators | Users uncomfortable with crypto casino backing |
| Multi-platform streamers (Kick + Twitch) | Those prioritizing independent/platform-neutral services |
| Gaming/IRL/content diversification seekers | Users who prefer ad-free without platform-level gambling integration |

---

## 🔍 Comparison to Alternatives

- **Twitch:** More established, stricter moderation, worse revenue split (50/50), Amazon-owned (US/China data concerns)
- **YouTube Live:** Google infrastructure (extensive telemetry), good discoverability
- **Trovo:** Microsoft-backed, smaller ecosystem
- **Open-source/self-hosted options:** Ongoing development but lack mainstream adoption

---

**Bottom line for your use case:** Kick offers attractive creator economics but carries reputational/security baggage from its gambling ties and Five Eyes jurisdiction. For viewing only, standard risks apply; for hosting streams, evaluate your comfort level with the ownership structure.

Would you like me to dig deeper into any specific aspect — like technical infrastructure, data retention policies, or comparisons with privacy-focused alternatives?

**USER:**
what are their domains

**ASSISTANT:**
Here's the domain footprint for **Kick Streaming** (owned by Kick Streaming Pty Ltd / Easygo Entertainment Pty Ltd, Melbourne, Australia — same parent as Stake.com), pulled from a public subdomain scan and Kick's own documentation:

## Core Domains (verified)

| Domain | Purpose | Infrastructure |
|--------|---------|----------------|
| `kick.com` / `www.kick.com` | Main platform | Cloudflare |
| `api.kick.com` | REST API | Cloudflare |
| `auth.kick.com` | Authentication/login | Cloudflare |
| `id.kick.com` | Identity service | Cloudflare |
| `stream.kick.com` | Livestream/video delivery + thumbnails | Cloudflare |
| `live.kick.com` | Live content | Cloudflare |
| `dashboard.kick.com` | Streamer dashboard | Cloudflare |
| `files.kick.com` | File storage | AWS/CloudFront |
| `assets.kick.com`, `static.kick.com`, `images.kick.com`, `content.kick.com` | Static content/CDN | Cloudflare / AWS |
| `feed.kick.com`, `ext.kick.com` | Feeds/extensions | AWS CloudFront |

## Supporting Subdomains (verified)

`about.` • `shop.` (Shopify-hosted, 23.227.38.74) • `admin.` • `cms.` • `web.` • `link.` • `status.` (Statuspage) • `developers.` / `dev.` • `docs.` • `help.` • `mobile.` • `tv.` • `search.` • `mail.` • `u.`

## Security Observations

- **Nearly all Kick infrastructure sits behind Cloudflare** — meaning TLS-encrypted proxied traffic that's harder to inspect or selectively block at the hostname level. If you want to block Kick wholesale, blocking `*.kick.com` plus the known IPs won't cover Cloudflare-shared ranges (which would break half the internet). DNS-level or Pi-hole/portmaster hostname blocking is the practical route.
- **`cf_clearance` cookie** appears in their API handshake requirements (visible in the GitHub endpoint documentation) — they use Cloudflare bot protection aggressively.
- **Third-party dependencies** confirmed: Cloudflare (proxy/CDN), AWS (CloudFront/S3 for files and images), Shopify (merch shop), Statuspage (uptime status).
- **Sister infrastructure:** Stake.com is the financial backer under the same parent (Easygo Entertainment). If you're cataloguing by operator, Stake's domains belong in the same ownership cluster. I don't have a verified subdomain list for Stake from these results, so I'd want to scan those separately rather than guess.

## For Your Blocklist Context

A conservative wildcard entry would be:

```
kick.com
*.kick.com
```

## Confirmed Trackers (per Kick's Privacy Policy)

**Operator: Google LLC (US)**

| Domain(s) | Purpose | Evidence |
|-----------|---------|----------|
| `google-analytics.com` / `analytics.google.com` | Google Analytics — session, device linking, behavioral flows, UTM paths, timestamps of first/last activity | Privacy policy names GA explicitly; they state they share "a unique identifier, like a user ID or hashed email address, with Google" |
| `doubleclick.net` | DoubleClick advertising cookie — display ad retargeting | Privacy policy names the DoubleClick advertising cookie explicitly, combined with GA "advanced features" |

**Operator: Cloudflare Inc. (US)**

| Domain | Purpose | Notes |
|--------|---------|-------|
| Kick domains themselves (`*.kick.com`) behind Cloudflare proxy | Bot management (`cf_clearance`, `__cf_bm` cookies) — passive fingerprinting-grade bot detection that profiles your browser | Not an "ad tracker" but absolutely a tracking layer; blocks scrapers and unusual clients |

**Operator: Salesforce (US)**

| Domain | Purpose |
|--------|---------|
| `status.kick.com` / Statuspage infrastructure | Incident/status comms — collects notification subscriber emails |

**Operator: Shopify Inc. (Canada 🇨🇦)**

| Domain | Purpose |
|--------|---------|
| `shop.kick.com` (resolves to Shopify IP 23.227.38.74) plus associated Shopify CDN/cart domains | Merch store — Shopify sets its own analytics and cart-tracking cookies |

## Likely But Not Explicitly Confirmed (labeled inference)

Since their privacy policy describes "display advertising" with Google and unnamed "third-party marketing partners," the typical Google Ads stack probably appears in network traffic on kick.com pages — but I couldn't verify actual script presence from these sources:

- `googletagmanager.com`
- `googlesyndication.com`
- `googleadservices.com`
- `adservice.google.com`

I'd verify these empirically rather than take them as gospel — your Portmaster setup is actually the ideal tool for this: load kick.com with logging on and check what gets resolved beyond `*.kick.com`.

## First-Party Tracking Signals (Kick's own)

From their terms/API traffic:
- **UTM tracking** — they explicitly record UTM source and "the electronic path you take... entering and exiting" (entry/exit page tracking)
- **Cross-device linking** — GA is used to "recognize you and link the devices you use" when logged in
- **Activity profiling** — timestamps, campaign schedules, emails opened, total logins, page/object click tracking
- **Hashed email to Google** — this crosses from aggregate analytics into identifiable-user territory; worth flagging in your catalogue

## Blocklist Recommendation

```
# Kick first-party (block whole platform if desired)
kick.com
*.kick.com

# Confirmed third-party trackers used by kick.com
doubleclick.net
*.doubleclick.net
google-analytics.com
*.google-analytics.com
analytics.google.com

# Likely Google ad stack (verify locally first)
googletagmanager.com
googlesyndication.com
googleadservices.com
```

Most of these Google domains are presumably already in your existing Google-ecosystem blocklists, so Kick wouldn't add much beyond its own first-party domains.

**One caveat:** the privacy policy also mentions unnamed "third-party marketing partners" and third-party cookies "for analytics and fraud prevention" — so there may be additional trackers they don't name. A live capture (Wireshark or Portmaster DNS log while loading kick.com) would close that gap definitively. Want me to search for any community-run DNS/request captures of kick.com to enumerate the unnamed third parties?

## Kick.com Official Email Addresses (verified from help.kick.com)

| Department | Email |
|------------|-------|
| General Support | `support@kick.com` |
| Technical Support | `techsupport@kick.com` |
| Subscription Enquiries | `subscriptions@kick.com` |
| Partnership Enquiries | `kickpartners@kick.com` |
| Ban Appeals | `appeals@kick.com` |
| Business Enquiries | `business@kick.com` |
| Career Opportunities | `careers@kick.com` |
| Verified Streamer Applications | `verify@kick.com` |
| **Youth Protection Officer** | `youthprotectionofficer@kick.com` |
| Press Enquiries | `press@kick.com` |
| **Cyber Security** | `security@kick.com` |
| Account Recovery | `recovery@kick.com` |

## DMCA / Legal (from kick.com/dmca-policy)

| Purpose | Email |
|---------|-------|
| DMCA takedown notices | `dmca@kick.com` |
| DMCA counter-notices | `dmca@kick.com` (same mailbox handles both) |
| Bot/viewbotting reports on channels | `support@kick.com` (per their Community Guidelines) |

## Notes for Your Catalogue

**Domain:** All addresses live on `kick.com` — no separate corporate mail domain observed (unlike larger companies that split off `@companyname.com` for staff).

**Tracking observation:** The Help Center page loads assets from `intercomcdn.com` (Intercom, US) — that's another third-party tracker dependency to add alongside Google Analytics and DoubleClick for the Kick cluster:

```
intercom.com
*.intercom.com
intercomcdn.com
*.intercomcdn.com
```

**Security relevance for your work:**
- `security@kick.com` exists specifically for vulnerability reports — since you're on the defensive side, that's your contact point if you ever find issues on their platform.
- `youthprotectionofficer@kick.com` reflects gambling-content exposure concerns — some jurisdictions require this officer role.
- **Phishing warning:** Because all legit Kick mail comes from `@kick.com`, any "Kick gift card", "Kick partnership offer", or "account suspension" email arriving from `kick-secure.com`, `kick-support.net`, `kickstream.co` or similar lookalike domains is almost certainly a scam. Worth flagging for CyberCrime-Stoppers awareness content — streaming-platform impersonation scams targeting creators (fake brand-deal emails) are a known pattern.
- I don't have verified records of fraudulent Kick-impersonation domains actively in circulation, so treat that last point as a caution based on general scam patterns rather than confirmed incidents.

**Ownership attribution for your records:** All these belong to Kick Streaming Pty Ltd ← Easygo Entertainment Pty Ltd (Melbourne, Australia), the same cluster as Stake.com.

Want me to run the Stake.com domain/subdomain breakdown next so the full Easygo cluster is grouped together in one entry?
