Grouped by operator with wildcards where they own whole subdomain trees. These are drawn from widely-used public blocklists (EasyList, AdGuard, StevenBlack hosts, OISD) and consistent with your existing telemetry catalogue.

## Google Advertising (USA — heavy cross-device tracking, ties ads to search/Gmail identity)
```
*.doubleclick.net
*.googlesyndication.com
*.googleadservices.com
*.googletagservices.com
*.googletagmanager.com
*.admob.com
*.adservice.google.com
*.pagead2.googlesyndication.com
*.doubleclick.*
*.googlesyndication.*
*.googleadservices.*
```
⚠️ Note: `googletagmanager.com` is also used for legit site analytics — blocking it rarely breaks sites, but some logins/payments may occasionally misbehave.

## Meta / Facebook Ads (USA — pixel-based cross-site tracking)
```
*.ads.facebook.com
*.an.facebook.com
*.connect.facebook.net
*.graph.facebook.com
*.ads-meta.*
*.ads.facebook.*
*.fbcdn.* (partial — hosts media too; consider selective rules)
*.atdmt.com (AT&T/multi-attribution, ties into Meta)
```

## Amazon Advertising (USA — runs one of the largest third-party ad exchanges)
```
*.amazon-adsystem.com
*.advertising.amazon.com
*.aax-us-east.amazon-adsystem.com
*.ads.aws.dev
*.assoc-amazon.com
```
Amazon-Adsystem serves ads on many publisher sites — safe to block wholesale.

## Microsoft Advertising (USA/EU — Bing Ads, Xandr legacy)
```
*.bing.com/commerce (rule-based)
*.adnxs.com (AppNexus/Xandr)
*.xandr.com
*.c.msn.com
*.bat.bing.com (clarity/retracking)
*.clarity.ms
```

## Apple / Miscellaneous US
```
*.iadsdk.apple.com
*.appleaux.apple.com
*.branch.io (app attribution, TikTok/OpenSea-linked)
*.appsflyer.com (mobile attribution — SlickLogin acquired by Google)
*.adjust.com (Germany-based, mobile attribution)
```

## Trade Desk & Programmatic Exchange Giants (USA)
```
*.adsrvr.org (The Trade Desk)
*.criteo.com / *.criteo.net (France — retargeting giant)
*.taboola.com (Israel)
*.outbrain.com (Israel)
*.rubiconproject.com (USA)
*.pubmatic.com (USA)
*.openx.net (USA)
*.smartadserver.com (France)
*.adform.net (Denmark)
*.casalemedia.com (Canada — CIX Media, Toronto)
*.indexexchange.com (Canada — Toronto HQ)
*.媒体/verizonmedia ad suite:
*.adtechjp.com
*.yieldmo.com
```
Canadian angle worth noting for you: Casale Media and Index Exchange are both Toronto-based — geopolitically neutral but still classic RTB trackers.

## TikTok / Bytedance (China — national-security-grade concern)
```
*.ads.tiktok.com
*.analytics.tiktok.com
*.tiktokcdn.com (careful — also hosts app media)
*.bytedance.com
*.byteoversea.com
*.musical.ly (legacy redirect)
*.byteglb.com
```
Strong recommend blocking ads/analytics paths; the CDN path is safe to inspect and selectively block.

## Yandex Advertising (Russia Federation — mandatory RU data-sharing risk)
```
*.an.yandex.ru
*.mc.yandex.ru
*.direct.yandex.ru
*.yastatic.net (careful — also serves Yandex front-end assets)
*.adfox.ru
*.metrika.yandex.*
*.appmetrica.yandex.com (mobile SDK embedded in MANY Western apps!)
```
🔴 **AppMetrica deserves special attention** — it's Yandex's mobile analytics SDK and ships inside apps distributed outside Russia. Nothing from Yandex should touch a device you care about.

## Mail.ru / VK (Russia Federation)
```
*.ad.mail.ru
*.top-fwz1.mail.ru
*.vk.com/rtrg (redirect pixel rule)
*.userapi.com (partial)
```

## Samsung / Smart-TV & Device Ads
```
*.ads.samsung.com
*.ads.samsungads.com
*.acr.samsung.com (Automatic Content Recognition — TV watches YOU)
*.tms.samsung.com
*.samsungacr.com
*.roku.com/api (telemetry paths)
*.wsall.roku.com
*.amazonfiretv.*
```
Smart-TV telemetry is worth a dedicated blocklist pass if you have any IoT screens on the family VLANs.

## Reward/Consent/Ad-Wrapper Services
```
*.scorecardresearch.com (Comscore, USA)
*.quantserve.com (Quantcast, USA)
*.moatads.com (Oracle Moat)
*.adsafeprotected.com (IAS)
*.doubleverify.com
*..bluekai.com (Oracle Data Cloud)
*.krxd.net (Salesforce Krux)
*.demdex.net (Adobe Audience Manager)
*.omtrdc.net (Adobe Analytics)
*.crwdcntrl.net (LiveRamp)
*.ads-twitter.com / *.static.ads-twitter.com (Twitter/X)
*.ads.linkedin.com / *.px.ads.linkedin.com
*.ads.youtube.com / *.ads.youtube.*
*.video.google.com (legacy video ad path)
```

## Known Malvertising / Fraud / Scam Infrastructure 🚨
Keep these blocked permanently — they routinely serve fake AV popups, tech-support scams, and phishing:
```
*.popads.net
*.popcash.net
*.propellerads.com
*.adcash.com
*.adsterra.com
*.hilltopads.net
*.onclickads.net
*.onclasrv.com
*.zedo.com
*.mgid.com
*.trafficjunky.net
*.exoclick.com (adult ad network — frequent malvertising)
*.clickadu.com
*.admaven.com
```

## Country TLD Risk Summary
- **RU (Yandex, Mail.ru)**: legally compelled to share data with Russian authorities — treat all RU-origin ad/analytics as hostile infrastructure. Block entire namespaces where feasible.
- **CN (Bytedance)**: same category; national intelligence law compels cooperation.
- **IL (Taboola, Outbrain)**: commercially aggressive but not state-compelled in the same way; privacy risk rather than sovereignty risk.
- **IR/KP equivalents**: don't appear in mainstream ad stacks, but `.ir` TLDs occasionally surface in scam redirects — a blanket TLD-level caution is defensible on your Omada ER605.
- **USA (Google/Meta/Amazon/Trade Desk)**: not state-surveillance in the same sense, but constitute the largest commercial surveillance apparatus in existence — which is exactly why they anchor your existing blocklists.

## Device-Appropriateness
- **Linux workstations / servers**: block everything above via hosts file + Portmaster, firewall routers safe-listing. No functional loss except occasional cosmetic ad slots.
- **Android (de-Google'd)**: AppMetrica, AppsFlyer, Adjust, Branch are the priority — they're SDK-embedded and slurp device fingerprints. DNS-level blocking helps but SDK calls sometimes bypass to hardcoded IPs.
- **Family VLANs: apply ad/fraud lists at the router level so smart TVs and guests get coverage before traffic ever leaves the LAN — pairs well with your existing UFW rules as defense-in-depth.
