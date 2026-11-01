# App Store assets

Summarized from Apple's App Store asset best practices page and the App Store Connect specification pages it links to. Paraphrased; dimensions and limits kept exact. Re-check the live specs before exporting — device lists change every year.

## Asset best practices
Source: https://developer.apple.com/app-store/asset-best-practices/

Asset types: **app previews** and **screenshots** (app in use / gameplay) and **creative assets** (brand, seasonal offers, new content — shown on the product page header, in search results and in featuring on iOS/iPadOS 27 and later). Read App Review Guideline **2.3 (Accurate Metadata)** and Apple's Advertising Policies first.

**Stay focused on the core experience**
- Content may go beyond the app UI but must relate to its functionality.
- **No specific prices, discounts, website URLs or © symbols.**
- **No unverifiable claims** (awards or recognition you didn't receive).
- **No logos or references to other platforms or marketplaces.**
- **No Apple recognitions** (Editor's Choice, App/Game of the Day, Apple Design Award) — Apple shows those itself.

**Design for everyone**
- Global, inclusive imagery; localize images and videos per region.
- **All assets must meet a 4+ rating** even if the app is rated higher: no explicit or harmful imagery, profanity, illegal drugs, self-harm, hate speech, stereotypes, sexually suggestive content, inflammatory religious commentary or misquoted religious texts.
- Violent games may show action but **no gore, graphic imagery or weapons pointed at a person or at the viewer**.

**Images**
- Current-looking photography/illustration; latest UI; strong composition with one clear focal point.
- Text: a short phrase that adds to the visual (not describes it); overlays can show input or highlight functionality; localize.
- Legible everywhere; keep key elements in the template **safe area** and the focal point **centered** to avoid clipping; check with the App Store Connect Preview tool.

**Videos**
- Pick a strong **poster frame** that works alone.
- Lead with the value proposition; pace cuts so people can follow; avoid quick cuts and fast motion (accessibility).
- **Loop seamlessly** (they autoplay and repeat).
- Assume **muted** playback — must work silently; audio is brand texture (short music loop, no sudden loud moments, loops cleanly).

**Per element** (keep a cohesive story: shared palette, iconography, fonts, message, tone)
- **App icon:** unique, recognizable at a glance, legible at every size (App Store, Spotlight, Home Screen). Build layered Liquid Glass icons in **Icon Composer** (see Foundations › App icons).
- **Product page header:** a single clear idea, not dense; designed for first-time visitors; can share a universal asset with the search result; A/B test via product page optimization. Templates: Figma, Photoshop, Pixelmator, Sketch.
- **Search results:** make the purpose obvious at a glance; show the firsthand experience (UI, content, gameplay). Without one, In-App Events, previews and screenshots appear instead.
- **In-App Events:** media for the **event card (16:9 landscape)** and **details page (9:16 portrait)** with visual continuity; design around the event badge (Challenge, Competition, Live Event, Major Update, New Season, Premiere, Special Event) without duplicating it.
- **Screenshots:** **up to 10** on the product page; up to **3** can appear in search results depending on orientation. Show the app in use with real detail, not accolades or calls to action; lead with the strongest features in a story-like sequence.
- **App previews:** **up to 3** per product page (up to 3 in search). Real UI or gameplay; grab attention in the first seconds; tell a beginning-middle-end story (features by popularity, game progression).

**Submitting:** via App Store Connect (with a version or in the **Asset Library**) or the App Store Connect API; use the product page preview tool. Creative assets also work on **custom product pages** and in **product page optimization** tests.

## Screenshot specifications
Source: https://developer.apple.com/help/app-store-connect/reference/app-information/screenshot-specifications

- **1–10 screenshots per device size**; .jpeg, .jpg or .png; **no alpha channels or transparency**.
- **Required:** iPhone — at least one for **iPhone with Dynamic Island (medium display)**; iPad (if supported) — at least one for **iPad 13-inch**.
- If the UI is the same across sizes and localizations, upload only the highest required resolution — App Store Connect scales down. Otherwise upload per size/localization.

| Display class | Example devices | Sizes (portrait; landscape is swapped) |
|---|---|---|
| iPhone Duo | iPhone Duo | outer 1398×2034; inner 2007×2853 (required from April 2027 for apps built with iOS 27.1 SDK+; earns an "optimized for iPhone Duo" badge) |
| Dynamic Island, large | iPhone Air, 18/17/16 Pro Max, 16 Plus, 15 Pro Max, 15 Plus, 14 Pro Max | 1260×2736, 1290×2796, 1320×2868 |
| Face ID, large | 14 Plus, 13/12/11 Pro Max, 11, XS Max, XR | 1284×2778, 1242×2688 |
| **Dynamic Island, medium (required)** | 18 Pro, 17 Pro, 17, 16 Pro, 16, 15 Pro, 15, 14 Pro | **1179×2556, 1206×2622** |
| Face ID, medium | 17e, 16e, 14, 13 (Pro/mini), 12 (Pro/mini), 11 Pro, XS, X | 1170×2532, 1125×2436, 1080×2340 |
| Home button, large | 8/7/6S/6 Plus | 1242×2208 |
| Home button, medium | SE (2nd/3rd gen), 8, 7, 6S, 6 | 750×1334 |
| Home button, 4" | SE (1st), 5S, 5C, 5 | 640×1096 (no status bar) or 640×1136 |
| Home button, 3.5" | 4S, 4 | 640×920 or 640×960 |
| **iPad 13" (required for iPad apps)** | iPad Pro (M5, M4, 6th–3rd, 1st gen), iPad Air (M4, M3, M2) | **2064×2752, 2048×2732** |
| iPad 12.9" | iPad Pro (2nd gen) | 2048×2732 |
| iPad 11" | iPad Pro 11", iPad Air 11", iPad (A16, 10th), iPad mini (A17 Pro, 6th) | 1488×2266, 1668×2420, 1668×2388, 1640×2360 |
| iPad 10.5" | iPad Pro 10.5", Air 3rd gen, iPad 7th–9th | 1668×2224 |
| iPad 9.7" | older iPads and iPad minis | 1536×2008/2048, 768×1004/1024 |

Missing sizes fall back to scaled screenshots from the nearest class. (Mac 16:10: 1280×800, 1440×900, 2560×1600, 2880×1800; Apple TV 1920×1080 or 3840×2160; Vision Pro 3840×2160; Apple Watch sizes on source page — one size across all localizations.)

## App preview specifications
Source: https://developer.apple.com/help/app-store-connect/reference/app-information/app-preview-specifications

- Optional; **up to 3 per device size and language**. Always shown **before** screenshots; a different aspect ratio than your screenshots moves it to "A Closer Look".
- **15–30 seconds; max 500 MB**; default poster frame at **5 s** (you can choose another); processing up to **24 hours**. Not available for iMessage-only apps.
- iOS previews may be portrait or landscape. Missing localized preview → next best language is used.
- **H.264:** 10–12 Mbps target, progressive up to High Profile Level 4.0, **max 30 fps**, .mov/.m4v/.mp4. **ProRes 422 (HQ only):** ~220 Mbps VBR, .mov.
- **Audio:** stereo, 256 kbps AAC (or PCM 16/24/32-bit for ProRes), 44.1 or 48 kHz, all tracks enabled (one 2-channel track, or two 1-channel tracks L/R).
- **Accepted resolutions** (upload these, not native device resolutions):
  - All modern iPhones (Duo, Dynamic Island, Face ID; 19.5:9): **886×1920** portrait / 1920×886 landscape.
  - iPhone with Home button large or 4": 1080×1920 / 1920×1080; medium: 750×1334 / 1334×750; 3.5": not supported.
  - iPad 13", 11", 10.5": **1200×1600** / 1600×1200; 12.9": 1200×1600 or 900×1200; 9.7": 900×1200 / 1200×900.
- Capture with a Face ID large-display iPhone or a 13" iPad and edit in iMovie/Final Cut Pro.

## Creative assets specifications
Source: https://developer.apple.com/help/app-store-connect/reference/app-information/creative-assets-specifications

No alpha channels or transparency in images.

| Placement | Format | Size | Video |
|---|---|---|---|
| Product page header | Image 21:9 | **3840×1646** (.jpeg/.jpg/.png) | 21:9, 3840×1646, 30 or 60 fps, **5–30 s**, .mov/.m4v/.mp4 |
| Product page header (universal) | Image 16:9 | **5244×2950** (.png) | — |
| Search results | Image 3:2 | **1920×1280 to 3840×2560** (.jpeg/.jpg/.png) | 3:2, same range, 30 or 60 fps, **5–30 s** |
| Search results (universal) | Image 16:9 | **5244×2950** (.png) | — |
| In-App Event card | 16:9 landscape | **1920×1080 to 3840×2160**, ≤500 MB | 16:9, 30/60 fps, **15–30 s** |
| In-App Event details | 9:16 portrait | **1080×1920 to 2160×3840**, ≤500 MB | 9:16, 30/60 fps, **15–30 s** |

Videos are **muted by default** (search results can't be unmuted; product page can) and **loop continuously**.

## In-App Events
Source: https://developer.apple.com/app-store/in-app-events/

Timely in-app events (competitions, premieres, livestreams…) shown as event cards on the product page, in search, and in editorial/personalized spots on Today, Games and Apps tabs; people can share, get notified at start, and download directly.
- **Limits:** up to **15 approved** events in App Store Connect; up to **10 published** at once; an event lasts **up to 31 days** and may be promoted **up to 14 days** before it starts; regional availability and times configurable; reviewed independently of app versions.
- **Good candidates:** challenges, competitions, special content launches. **Not:** repetitive daily tasks/rewards, price promotions without new content, general awareness campaigns.
- **Badges:** Challenge (reach a goal), Competition (rank/win), Live Event (real-time with new content), Major Update (significant new features/modes), New Season (new content building on existing), Premiere (first release of content), Special Event (anything else limited-time).
- **Metadata:** event name **≤30 characters**, title case, the event's real name (not a call to action like "Watch the livestream"; don't repeat the badge type); short description **≤50 characters**, sentence case (card); long description **≤120 characters**, sentence case (details page).
- No all caps, no repeated punctuation, no unverifiable claims ("the best", "#1") or filler ("game event"), **no specific prices** (rejection). Avoid text/logos in media; no borders or gradients (Apple applies crops/gradients); keep card and details media visually consistent; use licensed content; video gives a more dynamic preview (must loop).
- **Media:** card 16:9 (1920×1080 to 3840×2160), details 9:16 (1080×1920 to 2160×3840), images .jpg/.png, video .mov/.m4v/.mp4 at 30 or 60 fps.
- **Deep link:** universal link preferred (no URL shorteners/redirects); test it; send live events straight to the event, upcoming ones to an anticipation page, new users through onboarding first; always offer a way back to the main app.
- Purpose (all users / new / active / lapsed) informs personalization (processed on device); priority (high-priority events list first; otherwise by start time); mark if an extra IAP is required (for subscription apps, only if it costs beyond the subscription).
- Measure in App Analytics (downloads, sources, impressions, page views, opens, notification opt-ins).

## Creating your product page
Source: https://developer.apple.com/app-store/product-page/

- **App name:** simple, memorable, easy to spell, hints at function, distinctive; **≤30 characters**.
- **Icon:** simple, recognizable, no unnecessary detail; test variants.
- **Subtitle:** **≤30 characters**, concise value or key uses — not generic ("world's best app").
- **App previews:** up to 3, ≤30 s, device footage, localizable; autoplay muted — first seconds must hook; poster frame shows when not autoplaying.
- **Screenshots:** up to 10; the first 1–3 appear in search when there's no preview, so they must capture the essence; each later one = one main benefit; include a Dark Mode screenshot if supported.
- **Description:** a concise paragraph plus a short feature list in your brand voice; **the first sentence matters most** (visible without "more"); accolades at the end or in promo text; no keyword stuffing; **no prices**.
- **Promotional text:** **≤170 characters** above the description; editable anytime without a new version (news, limited-time sales, upcoming features); doesn't affect search.
- **Keywords:** **100 characters total**, comma-separated without spaces (spaces OK within phrases). Don't waste characters on plurals of existing words, category names, "app", duplicates or special characters. **Never** use unauthorized trademarks, celebrity names, irrelevant terms, competitor names, or offensive terms (common rejection cause).
- **In-app purchases on the product page:** up to **20** promoted items across IAP and subscriptions; display name **≤35 characters**, description **≤55 characters**, plus a promotional image.
- **What's New:** list features by importance; acknowledge feedback-driven fixes; add excitement.
- **Ratings:** system prompt up to **3 times per 365 days** (`SKStoreReviewController`/`RequestReviewAction`); respond to reviews in App Store Connect (only latest review/response shown); summary ratings are per territory.
- **Categories:** primary (most important for discoverability; determines the tab) and secondary; irrelevant choices may be rejected.
- **Localization:** localize description, keywords, previews, screenshots, and name per market.

## Custom product pages
Source: https://developer.apple.com/app-store/custom-product-pages/

- Up to **70** extra product page versions (iPhone and iPad), each with different screenshots, promotional text and/or previews, its own URL, full localization; usable in Apple Ads, editorial, StoreKit-rendered ads (`customProductPageIdentifier`) and pre-orders. Apple reports a 2.5-point average conversion lift.
- Assign keywords so a page appears in matching searches (intent must match; each keyword combination unique to one page). Optional deep link per page (iOS/iPadOS 18+).
- Metadata goes through review (independent of app updates). Measure impressions, conversion, retention and proceeds in App Analytics.

## Product page optimization
Source: https://developer.apple.com/app-store/product-page-optimization/

- Test up to **3 treatments** (alternate icons, screenshots, previews) against the original; randomly assigned traffic share; each person sees the same treatment for the test; localizable.
- One test at a time, up to **90 days**; can't edit after starting; new metadata needs App Review approval; **alternate icons must be in the shipped binary**. Tests without icon changes can be submitted without a new version.
- Reference name ≤64 characters. Change few elements per treatment to attribute results; more treatments take longer.
- Apply a winner only after ≥**90% confidence**; applying ends the test; ship any winning alternate icon in the next version.

## Discovery on the App Store
Source: https://developer.apple.com/app-store/discoverability/

- **Search ranking** factors: text relevance (title, keywords, primary category) and customer behavior (downloads, number and quality of ratings/reviews); suggested and trending searches.
- **Categories** drive browsing and which tab you appear in.
- **Today tab** editorial stories, App/Game of the Day; **Games and Apps tabs** with recommendations, charts, collections and autoplaying muted previews; promoted IAPs (up to 20) purchasable before download; App Store widget surfaces Today content.
- **Getting featured:** editors highlight new apps, significant updates, In-App Events, exclusives, cultural/seasonal moments and unique stories — pitch **6–8 weeks before** a launch or major update.

## App Store marketing guidelines (badges, product images, wording)
Source: https://developer.apple.com/app-store/marketing/guidelines/

Applies to marketing outside the store (web, ads, print, video) — and to how you word things in-app and in metadata.

**App Store badges**
- Download official badge artwork (50 localizations; "Download on the" / "Pre-order on the" translated, **"App Store" always in English**) — never make your own.
- **Preferred: black badge** (keep its gray border); always black when other platforms' badges appear, and **App Store badge first**. White alternative only when it's the sole badge and black looks heavy.
- One badge per layout/video, subordinate to the main message; **never modify, angle or animate it**. Swap pre-order badges for download badges at launch.
- Clear space **1/4 of badge height** (1/10 in very tight mobile banners); minimum height **10 mm print / 40 px onscreen**. One-color printing allowed with sufficient contrast.
- No icons/logos/images from apple.com; never the Apple logo in place of the word "Apple" or standalone.

**Product images**
- Use Apple-provided bezels of the **latest-generation** devices your app supports; minimum **25 mm print / 200 px onscreen** tall; correct relative scale.
- Use them unmodified — no reflections, shadows, highlights, things popping out of the screen, cropping, tilting, obstructing, animating, flipping, or turning them into buttons/icons. Copy goes beside, not on top.
- **Never show Apple devices next to competing products** (mention other platforms only in copy or badges). No 3D renders/simulations, illustrations (except instructional), die-cuts, food packaging, vehicle decals, or logotypes of Apple products. Generic device illustrations must avoid Apple-specific details (Home button, sensor housing, switches).
- **Screen content:** your app as it really runs, on the latest OS; never a blank screen; fictional account data; rights for all content. Status bar: full signal (or 5G if supported), full Wi-Fi, full battery. Show only **one** of your push notifications on the Lock Screen (none from other apps) and it must open your app. Don't show Home Screens unless showing your widget with no third-party content.
- **Photo/video:** authentic use, straight-on shots, accurate product color/shape, nothing fantastical; no gratuitous Apple logo; establishing shot then pan/zoom; simple fades/dissolves (no Multi-Touch-style transitions); start with the app open; "sequences shortened" disclaimer if edited; your app's sounds only, not device sounds; no cases/covers; no TV maker names for Apple TV.

**Wording**
- Focus on your app, not Apple features; clear copy with a download call to action.
- Say "[App] for iPhone" / "works with" / "compatible with" — **not "iPhone [App]"**. List only supported products. Company name → app name → products ("Company App for iPhone and iPad").
- Don't say iOS/macOS/etc. in marketing; never "smartphone"/"tablet" — use product names.
- Exact capitalization, singular, never all caps: **iPhone, iPad** (lowercase i even at sentence start), **Mac, MacBook Air/Pro, iMac**, **Apple Watch** (no "the", no "watch/time" puns), **Apple TV**, **Apple Vision Pro** (no "the", not a "headset"; call apps "spatial computing" — not AR/VR/XR/MR; can't be in your app name), **App Store** (only "the" as article; never "Apple App Store"/"iPhone App Store"; "available on/download from the App Store", not "at"), **Apple Pay, Wallet, Messages, Siri, Phone, Maps, iMessage**, **Apple In-App Purchase** (no "the"; use Apple's IAP marks).
- With other platforms, list Apple products first; never show Apple product images beside others.
- URLs may include Apple trademarks only after your name (company.com/app/iphone), never at the start (iphoneapp.com).
- **Never translate Apple trademarks** (App Store, Apple Pay, Apple Pencil, Apple TV, Apple Vision Pro, Apple Watch, iMac, iPad, iPhone, MacBook Air/Pro, Siri).

**Legal**
- US-only materials: ™/℠/® after each Apple trademark at **first body-copy mention** (not in headlines or on the badge); none outside the US.
- Credit lines wherever legal info appears, worldwide (e.g. "iPhone and iPad are trademarks of Apple Inc., registered in the U.S. and other countries."); credit Apple and the Apple Logo when using the badge.
- Nothing may falsely imply association with or endorsement by Apple.
