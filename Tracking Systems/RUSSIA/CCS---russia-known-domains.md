Russian domain landscape — comprehensive listing for your catalogue, This covers major operators, TLD structures, state-linked services, and security considerations relevant to your blocklist build.

## Russia — TLD Overview

| TLD | Description | Blocking Consideration |
|---|---|---|
| `.ru` | Main Cyrillic-script zone (Cyrillic: .рус also exists) | Over 3 million registered domains; blanket-blocking impractical |
| `.рф` | Full Cyrillic TLD (punycode `xn--p1ai`) | Often used for nationalist/state-aligned sites |
| `.su` | Soviet Union legacy TLD, still active | Historically abused for spam/phishing; lower registration friction |
| `.rf` | Sometimes misused for `.рф` confusion | Rare, but monitor |

**Practical reality:** DNS-layer blocking by TLD alone is noisy and imprecise. Your threat model should focus on **operator zones** (VK, Yandex, state-linked entities) rather than blanket `.ru` rules. Many legitimate Russian businesses operate globally; the risk profile varies significantly by entity.

---

## VK (Mail.ru Group) — Major Social/Internet Conglomerate

**Ownership & jurisdiction:** VK Company Ltd (formerly Mail.ru Group). State-controlled via Roskomnadzor-appointed leadership following the 2021 ownership restructuring. Based in Moscow, Russia. Subject to Russian federal data localization law (Article 24 of Federal Law No. 152-FZ).

**Primary domains:**

| Domain | Purpose |
|---|---|
| `*.vk.com` | VKontakte social network (Facebook equivalent) |
| `*.mail.ru` | Email portal, legacy gateway |
| `*.ok.ru` / `*.odnoklassniki.ru` | Odnoklassniki — older demographic social network |
| `*.my.mail.ru` | Mail.ru widget/embed platform |
| `*.livejournal.com` | LiveJournal (owned by Mail.ru since 2007) |
| `*.icq.com` / `*.sms.com` | ICQ messaging (revived 2013, declining) |
| `*.cloud.mail.ru` | Cloud storage |
| `*.disk.yandex.ru` | Wait — that's Yandex. Correction: `*.disk.mail.ru` is Mail.ru cloud |
| `*.games.mail.ru` | Gaming portal |
| `*.kinopoisk.ru` | Film/streaming service (Russia's IMDb + Netflix) |
| `*.avito.ru` | Classifieds marketplace |
| `*.delivery-club.ru` | Food delivery (acquired 2021) |
| `*.bt.ru` | Business technology portal |
| `*.rambler.ru` | Portal/search (separate entity, often conflated) |

**Subdomain classes worth noting:** `*.userapi.com` — VK media CDN; `*.vk.me` — shortlinks; `*.vkuser.net`, `*.vkusers.net` — app namespaces.

**Security posture:** Strong infrastructure TLS/HSTS. Not malware-distributing. Concerns stem from **state data access** (VK is legally required to comply with Russian FSB/SORM surveillance frameworks), not technical compromise. The EU designated VK under sanctions in 2022; Canadian restrictions apply through CSE guidance on high-risk vendors.

---

## Yandex — Russia's Google Equivalent

**Ownership & jurisdiction:** Yandex N.V. (formerly Dutch-incorporated, restructured 2022). Co-owner Pavel Prass increased stake in VK in 2026 per Reuters. Subject to same FSB/SORM obligations as VK.

**Recent events:** Between October 8–11, 2026, Ukrainian drone strikes hit three Yandex data centers (Sasovo, Kaluga, Vladimir) — two fully destroyed, third degraded. This caused widespread cloud outages affecting 64,000+ customers including government agencies and private firms (Ejércitos; Aviatrix; Meduza). Yandex updated terms to exclude liability for drone-strike disruptions.

**Primary domains:**

| Domain | Purpose |
|---|---|
| `*.yandex.ru` | Master domain — search, portal, homepage |
| `*.yandex.com` | International redirect (often blocked outside Russia) |
| `*.yandex.net` | CDN/static asset delivery |
| `*.yandex.cloud` / `*.cloud.yandex.ru` | Cloud infrastructure (competing with AWS/GCP) |
| `*.tax.yandex.ru` | Tax/financial services |
| `*.disk.yandex.ru` | Cloud storage (Yandex Disk) |
| `*.translate.yandex.ru` | Machine translation |
| `*.maps.yandex.ru`, `*.nav.yandex.ru` | Navigation/maps |
| `*.metro.yandex.ru` | Transit info |
| `*.taxi.yandex.ru`, `*.go.yandex.ru` | Ride-hailing |
| `*.food.yandex.ru` | Food delivery |
| `*.market.yandex.ru` | Marketplace/e-commerce |
| `*.music.yandex.ru` | Music streaming |
| `*.video.yandex.ru` | Video platform |
| `*.zen.yandex.ru` / `*.dzen.ru` | Content/news aggregator |
| `*.passport.yandex.ru` | Unified login/identity |
| `*.id.yandex.ru` | Identity service |
| `*.alice.yandex.ru` | Voice assistant (Alexa equivalent) |
| `*.browser.yandex.ru` | Yandex Browser |
| `*.autobot.yandex.ru` | Autonomous vehicle project |
| `*.robot.yandex.ru` | Robotics/AI lab |

**Zen sale:** August 2026, Yandex agreed to sell its news aggregator Zen and homepage yandex.ru to state-controlled VK — tightening Kremlin oversight of independent media access (Yahoo Finance).

**Infrastructure notes:** Yandex operates data centers in Moscow, St. Petersburg, Novosibirsk; some redundancy in Kazakhstan (per Meduza report on drone strikes). Customers advised to back up to Selectel, K2Cloud, VK Cloud.

---

## Ozon & E-Commerce Sector

**Ozon.ru** — Often called "Russia's Amazon." Listed on Nasdaq until delisted March 24, 2026 along with HeadHunter, Qiwi, Cian (Yahoo Finance). Still operational domestically. Appeals filed against delisting.

| Domain | Purpose |
|---|---|
| `*.ozon.ru` | Master marketplace |
| `*.ozon.global` | International shipping |
| `*.wildberries.ru` | Wildberries — rival marketplace (also targeted in cyber/physical attacks) |
| `*.lamoda.ru` | Fashion e-commerce |
| `*.citilink.ru` | Electronics retailer |
| `*.dns-shop.ru` | Computer hardware retail |

---

## Banking & Financial Services (Sanctions-Sensitive)

**Sberbank (Sber)** — Largest Russian bank, state-owned. Domains: `*.sberbank.ru`, `*.sber.ru`, `*.sber.me`, `*.sber.ru` (shortened). EU/US/Canada sanctioned. Transaction monitoring required for any business dealings.

| Domain | Operator | Status |
|---|---|---|
| `*.sberbank.ru` | Sberbank | State-linked, sanctioned |
| `*.sber.ru` | Sberbank | State-linked, sanctioned |
| `*.alfabank.ru` | Alfa Bank | Private, but subject to secondary sanctions risk |
| `*.vtb.ru` | VTB Bank | State-owned, sanctioned |
| `*.gazprombank.ru` | Gazprombank | State-linked energy finance |
| `*.tinkoff.ru` | Tinkoff Bank | Private fintech, lesser sanctions exposure |
| `*.qiwi.com` | Qiwi | Fintech, delisted 2026, sanctioned |
| `*.rbk.ru` | RBK (Financial) | Media, not financial services |

**Note for your compliance stance:** As a Canadian citizen, OFAC/EU/CANADA sanction lists matter for financial relationships, not just DNS blocking. Any connection to these entities could trigger secondary sanctions depending on your business activities.

---

## Telecommunications & ISP Infrastructure

| Domain | Operator | Notes |
|---|---|---|
| `*.mts.ru` | MTS (Mobile TeleSystems) | Largest mobile carrier |
| `*.beeline.ru` | Beeline (VimpelCom) | Second-largest mobile |
| `*.megafon.ru` | MegaFon | Third-largest mobile |
| `*.rostelecom.ru` | Rostelecom | State-controlled backbone ISP |
| `*.dom.ru` | Dom.ru | Regional ISP |
| `*.rt.ru` | Rostelecom consumer brand |
| `*.tkart.net` | Traffic analytics/tracking |

MegaFon was mentioned in Meduza report as purchasing data center capacity post-drone strikes. Rostelecom is directly state-controlled under Ministry of Digital Development.

---

## Government & State-Linked Zones

These are higher-priority blockers if you're concerned about influence operations or data access:

| Domain | Agency/Purpose |
|---|---|
| `*.gov.ru` | Federal government portal |
| `*.minjust.ru` | Ministry of Justice |
| `*.mvd.ru` | Interior Ministry |
| `*.fsb.ru` | Federal Security Service (direct surveillance org) |
| `*.svr.ru` | Foreign Intelligence Service |
| `*.roscosmos.ru` | Space agency |
| `*.rkn.gov.ru` | Roskomnadzor (censorship authority) |
| `*.kremlin.ru` | Presidential administration |
| `*.government.ru` | Cabinet of Ministers |
| `*.gosuslugi.ru` | Public services portal |
| `*.sfy.ru` | Supreme Court |
| `*.ras.ru` | Russian Academy of Sciences |

**Roskomnadzor:** The censorship/enforcement arm that maintains the "Unified Register of Prohibited Information" (blocklist). Any site added to that register is technically required to be blocked by Russian ISPs.

---

## Media & Information Operations

**State-aligned media networks:**

| Domain | Entity |
|---|---|
| `*.rt.com` | RT (Russia Today) — state-funded international news |
| `*.sputniknews.com` | Sputnik — radio/news service |
| `*.tass.ru` | TASS — state news agency |
| `*.ria.ru` | RIA Novosti — state news |
| `*.interfax.ru` | Interfax — semi-state wire service |
| `*.lenta.ru` | Lenta.ru — formerly independent, editorial changes 2014 |
| `*.gazeta.ru` | Gazeta.ru — government-friendly |
| `*.km.ru` | KM.ru — aggregator |

**Independent/Exiled media (higher trust, but may be blocked in Russia):** `*.meduza.io`, `*.novayagazeta.eu`, `*.theins.ru`, `*.proekt.media`, `*.iStories.media`. These are worth noting because Russian state media frequently targets them for disinformation campaigns.

**Telegram:** Pavel Durov founded Telegram as a privacy-first messenger, rejected Russian FSB demands for encryption keys in 2018. Telegram was briefly blocked in Russia 2018–2020 (unsuccessfully). Domain: `*.telegram.org`, `*.t.me`, `*.tgstat.com` (analytics). Recent regulatory pressure: France/Australia seeking obligations around illegal content moderation (Carnegie Endowment).

---

## Threat Assessment & Blocking Recommendations

### Jurisdiction Concerns

**Russian Federation:**
- **Surveillance law:** Federal Law No. 152-FZ requires all personal data on Russian citizens to be stored on servers physically located in Russia (data localization). Roskomnadzor enforces this.
- **SORM framework:** State Security System of Measures for Operational-Investigative Activities mandates telecom/ISP infrastructure provide FSB direct access to all traffic metadata and content.
- **Sovereign Internet Law (2019):** Enables Russia to disconnect from global internet and operate autonomously. Tested annually.

**For your threat model:** Any service operating in Russia is subject to FSB warrants without judicial oversight. This differs from US jurisdiction (requires court order, though FISA §702 allows bulk collection). The practical difference: Russian authorities can seize data without notice to the company or user.

### Cybersecurity Profile

**Not malware distribution:** Major Russian tech zones (`yandex.ru`, `vk.com`, `mail.ru`) are not malware-hosting platforms. You won't get payloads from these domains themselves.

**Real threats:**
1. **Phishing clones:** `yandex-login.ru`, `vk-auth.ru`, `mail-r.ru` (hyphen typosquats) are common credential-harvesting vectors
2. **Botnet C2 infrastructure:** Historically, `.ru` and `.su` zones hosted significant botnet command servers. Less prominent in 2026, but still monitored by Europol/ENISA
3. **Disinformation amplification:** EEAA March 2026 report identified 540 interference incidents, 29% attributed to Russia across websites, social media, automation (Ejércitos)
4. **Supply-chain attacks:** SolarWinds-style compromises are harder to rule out for state-linked vendors given opaque corporate structures

### Blocking Tiers

| Tier | Domains | Rationale |
|---|---|---|
| High priority | `*.fsb.ru`, `*.rkn.gov.ru`, `*.mvd.ru`, `*.svr.ru` | Direct surveillance/enforcement organs |
| Medium-high | `*.vk.com`, `*.mail.ru`, `*.yandex.ru`, `*.rt.com`, `*.sputniknews.com` | State data access + disinformation surfaces |
| Medium | `*.sberbank.ru`, `*.vtb.ru`, `*.gazprombank.ru`, `*.qiwi.com` | Sanctioned financial entities |
| Low priority | `*.mts.ru`, `*.megafon.ru`, `*.dom.ru` | Telecoms (traffic visibility, not direct data theft) |
| Optional | `*.ok.ru`, `*.avito.ru`, `*.ozon.ru`, `*.wildberries.ru` | Commercial services with lesser state ties |
| Informational | `*.roscosmos.ru`, `*.ras.ru` | Academic/space, no tracking function |

**Wildcard caution:** Don't blanket-block `*.ru` or `*.su` without testing — you'll break legitimate business sites, open-source projects hosted on Russian git mirrors, and research collaborations. Per-operator blocking is cleaner.

---

## Geopolitical Context for Canadian Users

**Your position:** Canadian citizenship means PIPEDA applies to your data, but **no extraterritorial shield** protects you from Russian surveillance if you voluntarily connect to Russian services.

**Current tensions (October 2026):**
- **Yandex drone strikes:** Ukraine targeting Russian digital infrastructure as part of broader campaign against strategic assets. Shows kinetic attack vectors now exist (Meduza, Carnegie Endowment).
- **VK-Yandex consolidation:** State tightening control over independent media through the Zen/yandex.ru sale (August 2026). More content will flow through VK's centralized moderation.
- **Nasdaq delistings:** Russian tech firms removed from US exchanges March 2026, reducing Western investor oversight (Yahoo Finance).

**For your blocklist philosophy:** Given your existing stance against US Big Tech surveillance, the question is whether Russian state-linked services present equal, greater, or lesser concern. Key differences:

- **US:** FISA §702 allows bulk collection of non-US persons' data (including Canadians), with limited judicial oversight
- **Russia:** FSB warrantless seizure possible, no notice required, data localization ensures physical control
- **Trade-off:** US services are better engineered for encryption-in-transit; Russian services may be more openly compliant with state requests

Neither is "safe" from surveillance in a adversarial threat model. The distinction is jurisdiction and operational transparency.

---

## Additional Russian Ecosystems to Enumerate

I have gaps on these areas — worth capturing live from packet captures if you're building a definitive list:

| Category | Unknown domains to verify |
|---|---|
| **Messaging apps** | Telegram onion services, VK Messenger variants |
| **Cloud providers** | Selectel, K2Cloud, Timeweb Cloud domains |
| **Cryptocurrency exchanges** | Garantex, BestChange (sanctioned 2022–2023) |
| **Torrent/filesharing** | Rutracker.org (blocked in Russia but accessible abroad) |
| **Anonymous hosting** | Various offshore Russian registrars |

Want me to:
1. **Continue to China domains** (largest TLD volume after .ru/.su combined)?
2. **Build the deduplicated master list** combining Google, Meta, and Russian sets?
3. **Cover China next** (since you're comparing US vs. non-US tech ecosystems)?
4. **Pull in specific threat intel feeds** for Russian botnet/C2 indicators?

Your call on sequencing.
