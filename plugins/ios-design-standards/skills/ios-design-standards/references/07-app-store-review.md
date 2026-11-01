# App Store Review Guidelines

Summarized from Apple's App Review Guidelines, organized by guideline number so a design can be checked for rejection risk. Paraphrased; numbers and hard limits kept exact. **Before submitting, always re-check the live page** — Apple updates it often: https://developer.apple.com/app-store/review/guidelines/

## Introduction and general principles
- Goal: a safe store for users and a fair opportunity for developers. Apps are human-reviewed and malware-scanned. In some regions apps can also be distributed via alternative marketplaces/web with **Notarization** (a subset of these rules applies).
- Kids and teens use the App Store — provide age-appropriate experiences; parental controls depend on you too.
- The App Store isn't for apps meant only for friends and family (use Xcode or Ad Hoc distribution).
- All viewpoints welcome if respectful; Apple rejects content it considers "over the line".
- Cheating (tricking review, stealing data, copying, manipulating ratings/discovery) → removal and expulsion from the Developer Program.
- **You're responsible for everything in your app, including ad networks, analytics and third-party SDKs.**
- Some capabilities are entitlement-only (e.g. CarPlay Audio, HyperVisor, Privileged File Operations).

## Before You Submit — checklist
- Test for crashes and bugs on compatible devices; configure In-App Purchases for review.
- Complete, accurate metadata; current contact info.
- Give reviewers **full access**: an active demo account or a fully featured demo mode, plus any hardware/resources (login credentials, sample QR code).
- Backend services live during review.
- Explain non-obvious features and IAPs in **App Review notes** (with documentation where useful).
- Provide documentation for regulated features.
- Follow related docs: HIG, App Store Connect/App Review help, iCloud backup and file system docs, App Store marketing, Apple Pay and Add to Apple Wallet guidelines, Apple trademark guidelines.
- Apps that stop working or aren't maintained get removed.

## 1. Safety

**1.1 Objectionable content** — rejected if offensive, upsetting, disgusting or creepy, including:
- 1.1.1 Defamatory, discriminatory or mean-spirited content about religion, race, sexual orientation, gender, origin or other groups (professional political satire/humor generally exempt).
- 1.1.2 Realistic depictions of people/animals killed, maimed, tortured or abused, or encouraging violence. Game "enemies" may not solely target a real race, culture, government, corporation or other real entity.
- 1.1.3 Encouraging illegal/reckless weapon use or facilitating firearm/ammunition purchases.
- 1.1.4 Overtly sexual or pornographic material, including "hookup" apps or anything facilitating prostitution or trafficking.
- 1.1.5 Inflammatory religious commentary or misquoting religious texts.
- 1.1.6 False information or trick features (fake trackers, fake device data) — "for entertainment" disclaimers don't help; anonymous/prank calling or SMS apps are rejected.
- 1.1.7 Profiting from current tragedies (conflicts, terror attacks, epidemics).

**1.2 User-generated content** (social, UGC platforms, AI content creation) must have:
- Filtering of objectionable content before posting
- A way to **report** content, with timely responses
- The ability to **block** abusive users
- **Published contact information**
- Apps used mainly for porn, Chatroulette-style or random/anonymous chat, "hot-or-not" objectification, threats or bullying don't belong. Web-sourced UGC may show incidental NSFW content only if hidden by default and enabled by the user on your website. You must remove violating content; failure can mean removal and Code of Conduct violations.
- **1.2.1 Creator content** (non-developer creators' videos, articles, audio, casual games inside your app) is treated as UGC: must follow 1.2 moderation and 3.1.1 payments; tell users which content costs extra; (a) let users identify content above the app's age rating and **restrict underage users by verified or declared age**.

**1.3 Kids Category**
- No links out, purchases or other distractions unless behind a **parental gate**. Once in Kids, you must keep meeting the rules in updates even if you leave the category.
- Comply with children's privacy laws worldwide. **No sending personal or device info to third parties. No third-party analytics or advertising** — limited exceptions: analytics that collect no IDFA or identifying info about kids/location/devices; contextual ads from services with public Kids policies and human review of creatives.

**1.4 Physical harm**
- 1.4.1 Medical apps get extra scrutiny: disclose data and methodology for accuracy claims (unvalidated → rejected). **Sensor-only claims of X-rays, blood pressure, temperature, blood glucose or blood oxygen aren't allowed.** Remind users to consult a doctor; submit regulatory clearance if you have it.
- 1.4.2 Drug dosage calculators only from manufacturers, hospitals, universities, insurers, pharmacies or other approved entities, or with FDA/equivalent approval.
- 1.4.3 No encouraging tobacco/vape, illegal drugs or excessive alcohol (never to minors); no facilitating sales of controlled substances (except licensed pharmacies and licensed/legal cannabis dispensaries) or tobacco.
- 1.4.4 Only law-enforcement-published DUI checkpoints; never encourage drunk driving or speeding.
- 1.4.5 Don't urge risky activities (bets, challenges) or risky device use.

**1.5 Developer information:** easy contact in the app and Support URL (important for classroom apps); Wallet passes need valid issuer contact info and a dedicated certificate for the brand owner.

**1.6 Data security:** appropriate security to prevent unauthorized use, disclosure or access (see 5.1).

**1.7 Reporting criminal activity:** must involve local law enforcement and only where that's active.

## 2. Performance

**2.1 App completeness**
- (a) Submit final versions (including pre-orders) with complete metadata and working URLs — **no placeholder text, empty websites or temporary content**. Test on device; provide demo account info and keep the backend on. A built-in demo mode instead of an account needs Apple's prior approval and must show all features. Crashing or obviously broken binaries are rejected.
- (b) IAPs must be complete, current, visible to the reviewer and working; explain any that can't be found.

**2.2 Beta testing:** no demos, betas or trials on the App Store — use **TestFlight** (builds must be intended for public release and follow the guidelines; never distribute to testers for compensation, including crowdfunding rewards; submit significant beta updates for TestFlight review).

**2.3 Accurate metadata** (description, screenshots, previews, privacy info must reflect the core experience and stay current)
- 2.3.1 (a) Describe new features specifically in Notes for Review (generic notes rejected). Misleading marketing (fake features like iOS "virus scanners", false prices) → removal and account termination; (b) egregious/repeated → expulsion.
- 2.3.2 Make clear in description, screenshots and previews which featured items/levels/subscriptions cost extra. Promoted IAPs need public-appropriate names, screenshots and descriptions and must handle the purchase on launch (`SKPaymentTransactionObserver`).
- 2.3.3 **Screenshots show the app in use** — not just title art, login or splash screens. Text/image overlays are OK (e.g. touch points, Apple Pencil).
- 2.3.4 **Previews use only screen captures of the app** (Stickers/iMessage may show Messages); narration and text/video overlays allowed.
- 2.3.5 Choose the right category (Apple may change it).
- 2.3.6 Answer age-rating questions honestly; comply with local media rating/warning rules.
- 2.3.7 Unique name; accurate keywords; **no stuffing with trademarks, popular app names, prices or irrelevant phrases. App names max 30 characters.** Name, subtitle, screenshots and previews must not contain prices or text not appropriate to that metadata type. Subtitles: no inappropriate content, other-app references or unverifiable claims.
- 2.3.8 **All metadata (icons, screenshots, previews, IAP icons) must be 4+ appropriate** even if the app is rated higher. "For Kids"/"For Children" reserved for the Kids Category. Keep name and all icons (including alternates) consistent.
- 2.3.9 Secure rights to all materials; show **fictional account data, not real people's**.
- 2.3.10 Focus on Apple platforms — **no names, icons or imagery of other mobile platforms or alternative marketplaces** unless there's approved interactive functionality; no irrelevant info.
- 2.3.11 Pre-orders must be complete and match what's delivered; restart pre-orders after material changes (e.g. business model).
- 2.3.12 "What's New" must describe significant changes (generic text OK only for bug/security/performance fixes).
- 2.3.13 In-app events: use an App Store Connect event type; accurate event-specific metadata; happen at the stated times in all storefronts; monetization per section 3; deep links to the right place.
- 2.3.14 **Creative assets** (product page header, search): must relate to app content/functionality or brand, follow metadata rules, be all-ages, no misleading references to other apps, no unverifiable claims, **no specific or discounted pricing**. See App Store asset best practices.

**2.4 Hardware compatibility**
- 2.4.1 **iPhone apps should run on iPad whenever possible.**
- 2.4.2 Power-efficient; no rapid battery drain, excess heat or resource strain (e.g. don't encourage charging under a pillow, excessive SSD writes); no unrelated background processes like **crypto mining** (including in ads).
- 2.4.3 Apple TV apps must work with the Siri Remote or game controllers; disclose required controllers in metadata.
- 2.4.4 **Never suggest or require a device restart or unrelated system-setting changes** (e.g. turning off Wi-Fi or security features).
- 2.4.5 Mac App Store extras: sandboxing; Xcode packaging only; no auto-launch without consent; no downloading code/kexts; no root escalation; no license screens/keys/copy protection; updates only via the Mac App Store; current OS; all localizations in one bundle.

**2.5 Software requirements**
- 2.5.1 **Public APIs only**; run on the current OS; phase out deprecated tech; use frameworks for their intended purpose and mention integrations in the description (HomeKit for home automation, HealthKit for health with Health app integration).
- 2.5.2 Self-contained bundles; don't read/write outside the container; **don't download or execute code that changes features** (limited exception: educational coding apps where the code is fully viewable and editable).
- 2.5.3 No malware or code that disrupts the OS, hardware, Push Notifications or Game Center.
- 2.5.4 Background modes only for their intended purpose (VoIP, audio, location, task completion, local notifications…).
- 2.5.5 **Must work on IPv6-only networks.**
- 2.5.6 Web browsing must use WebKit (alternative engines need an entitlement — EU and Japan).
- 2.5.8 No alternate home screen/desktop environments.
- 2.5.9 Don't alter or disable standard switches (volume, Ring/Silent) or native UI behaviors; don't block links out to other apps.
- 2.5.11 SiriKit/Shortcuts: register only intents you can handle yourself and users would expect; vocabulary and aliases must relate to your app/company (no generic terms or third-party names); resolve requests directly — **no ads or marketing between request and fulfillment**; disambiguate only when needed.
- 2.5.12 CallKit/SMS fraud extensions: block only confirmed spam; explain blocking criteria in marketing text; use the data only to run/improve the feature (no tracking, profiles or selling).
- 2.5.13 Facial-recognition login must use **LocalAuthentication** (not ARKit etc.) where possible, with an **alternative method for users under 13**.
- 2.5.14 **Explicit consent and a clear visual/audible indicator whenever recording or logging user activity** (camera, mic, screen recording, other inputs).
- 2.5.15 File pickers should include the Files app and iCloud documents.
- 2.5.16 Widgets, extensions and notifications must relate to the app; (a) all App Clip functionality must also be in the main app; **no ads in App Clips**.
- 2.5.17 Matter: pair through Apple's Matter framework; non-Apple Matter components must be CSA-certified.
- 2.5.18 **Ads only in the main app binary** — not in extensions, App Clips, widgets, notifications, keyboards or watchOS apps. Ads must match the age rating, let users see targeting info without leaving the app, and **never target using sensitive data** (health/HealthKit, ClassKit/school data, kids). **Interstitials must be clearly labeled as ads, not trick users, and have an easily visible close/skip button large enough to dismiss.** Provide a way to report inappropriate ads.
- 2.5.19 **No hidden, dormant or undocumented features** (obfuscating them → removal and termination).

## 3. Business

- Explain non-obvious business models in metadata and review notes. Clear rip-offs and irrationally high prices are rejected.
- Manipulating reviews or rankings (paid, incentivized, filtered or fake feedback, or third-party services) → possible expulsion.

**3.1 Payments**

**3.1.1 In-App Purchase** — required to unlock features or functionality (subscriptions, in-game currency, levels, premium content, full-version unlocks).
- **Not allowed as unlock mechanisms:** license keys, AR markers, QR codes, cryptocurrencies/wallets, etc.
- Tipping developers/creators may use IAP currencies.
- **Purchased credits/in-game currencies may not expire**; provide a **restore** mechanism for restorable purchases.
- Gifting IAP items is allowed (refund only to the original purchaser; no exchanges).
- **Loot boxes / randomized items must disclose the odds before purchase.**
- Digital gift cards/vouchers redeemable for digital goods must use IAP (physical mailed gift cards may use other payment).
- Non-subscription free trials: a Non-Consumable IAP at Price Tier 0 named **"XX-day Trial"**; before the trial, state its duration, what will be lost at the end, and the costs for full access.
- NFTs: may sell NFT services (minting, listing, transferring) via IAP; viewing own NFTs OK if ownership doesn't unlock features; browsing others' collections OK but (outside the US storefront) no calls to action toward non-IAP purchases.
- **3.1.1(a) Link to other purchase methods:** in specific regions, StoreKit External Purchase Link Entitlements (or Music Streaming Services Entitlement) allow a link to permitted destinations, including telling users it may be cheaper. **Not required on the United States storefront**, where buttons/links/calls to action to other purchase methods are allowed. Everywhere else (without the entitlement), no buttons, links or calls to action to non-IAP purchasing. Misleading use → removal.

**3.1.2 Subscriptions** (any category)
- (a) Must provide **ongoing value**; **period at least 7 days**; available on **all the user's devices**. Good uses: new levels, episodic content, multiplayer, substantive updates, large/updated media libraries, SaaS, cloud. May sit alongside à la carte purchases. Game streaming subscriptions: games downloaded from the App Store, no double charging, don't disadvantage non-subscribers.
- **Never require extra tasks to get what was paid for** (posting to social media, uploading contacts, check-ins).
- Subscriptions may include consumables or discounted consumables.
- **Switching to subscriptions must not remove functionality existing users already paid for.**
- Free trials configured in App Store Connect.
- Scams, false pretenses, bait-and-switch → removal and possible expulsion.
- Carrier bundles only with Apple's prior approval (rules on consumables and plan termination).
- (b) Seamless upgrades/downgrades; prevent subscribing to multiple variations of the same thing.
- (c) **Before asking to subscribe, clearly describe what the user gets for the price** (issues per month, storage, access level) and meet Schedule 2 of the Developer Program License Agreement.

**3.1.3 Other purchase methods** — these may use non-IAP payment, but inside the app may not encourage non-IAP purchasing (except the US storefront and 3.1.1(a)/3.1.3(a)); you may email your users about other methods outside the app.
- (a) **Reader apps** (magazines, newspapers, books, audio, music, video): access previously purchased content/subscriptions; free-tier sign-up and account management allowed; External Link Account Entitlement for a link to your own site (not needed for the US storefront).
- (b) **Multiplatform services:** access content bought on other platforms/web — if those items are also available as IAP in the app.
- (c) **Enterprise services** sold directly to organizations for employees/students (consumer, single-user and family sales must use IAP).
- (d) **Person-to-person real-time services** between two individuals (tutoring, medical consults, real estate tours, fitness training) may use other payments; **one-to-few or one-to-many must use IAP**.
- (e) **Physical goods and services consumed outside the app must NOT use IAP** — use Apple Pay or card entry.
- (f) Free companion apps to paid web tools (VoIP, cloud storage, email, web hosting) — no in-app purchasing or calls to action.
- (g) Ad campaign management apps (but buying "boosts" displayed in the same app must use IAP).

**3.1.4 Hardware-specific content:** features that need specific hardware (telescope) may unlock without IAP; optional companion-product features (toys) may too if an IAP option also exists. Never require buying unrelated products or doing marketing to unlock features.

**3.1.5 Cryptocurrencies:** (i) wallets only from developers enrolled as organizations; (ii) **no on-device mining**; (iii) exchanges only where licensed; (iv) ICOs, crypto futures and crypto-securities only from established/approved financial institutions; (v) no crypto rewards for tasks (downloading apps, referrals, social posting).

**3.2 Other business model issues**
- **3.2.1 Acceptable:** promoting your own apps (not just a catalog); curated third-party app collections for a specific approved need with robust editorial content; expiring approved rentals (films, TV, music, books) — nothing else may expire; Wallet passes for payments, offers or ID; insurance apps (free, legally compliant, no IAP); approved nonprofits fundraising in-app with Apple Pay and disclosure of fund use and tax receipts; optional person-to-person monetary gifts with 100% to the recipient (if tied to digital content → IAP); financial trading/investing apps submitted by licensed institutions.
- **3.2.2 Unacceptable:** App Store-like storefronts or general collections of third-party apps/extensions; artificially inflating ad impressions/clicks or apps mainly for showing ads; collecting charity funds in-app unless an approved nonprofit (others must be free and collect outside the app via Safari or SMS); arbitrarily restricting users by location or carrier; manipulating visibility/rank on other services; **binary options** trading; unlicensed CFD/FOREX; personal loans that don't disclose terms (max APR, due date), **charge over 36% APR** including fees, or require full repayment in **60 days or less**; **forcing users to rate, review or download other apps to access functionality** (incentivizing in-app actions like completing a level or watching an ad is fine).

## 4. Design
Minimum standards for approval; keep apps updated — degraded or broken apps can be removed anytime.

**4.1 Copycats**
- (a) Don't copy popular apps or make minor name/UI tweaks to someone else's app.
- (b) Impersonating other apps or services violates the Code of Conduct.
- (c) **Don't use another developer's icon, brand or product name in your icon or app name** without their approval.

**4.2 Minimum functionality** — must be more than a repackaged website; useful, unique, "app-like", with lasting value. Single songs/movies → iTunes Store; books/game guides → Apple Books.
- 4.2.1 ARKit apps need rich, integrated AR — not just dropping a model or replaying an animation.
- 4.2.2 Apps shouldn't primarily be marketing, ads, web clippings, content aggregators or link collections (catalogs excepted).
- 4.2.3 (i) Must work without installing another app; (ii) **disclose the size and prompt before downloading extra resources needed at first launch.**
- 4.2.6 Template/app-generator apps are rejected unless submitted by the content provider itself; or use one aggregated "picker" app for all clients.
- 4.2.7 Remote desktop clients mirroring specific software: only to user-owned PCs/consoles on the local network; software fully executed and rendered on the host; account management from the host; no iOS/App Store-like UI or store for unowned software; cloud thin clients not allowed.

**4.3 Spam**
- (a) **No multiple bundle IDs of essentially the same app** (one city per app, etc.) — use one app with IAP variations.
- (b) No apps indistinguishable from what's already widely available. Saturated categories (dating, flashlight, sound effects, wallpaper, simple timers, fortune telling) need a meaningfully different or better experience. Low-effort apps (drinking games, Kama Sutra, fart/burp apps) are rejected; repeat submissions risk expulsion.

**4.4 Extensions** — follow extension docs; include help/settings where possible; disclose extensions in marketing text; **no marketing, ads or IAP inside extensions**.
- 4.4.1 **Keyboard extensions must:** provide real keyboard input; follow sticker rules for images/emoji; provide a way to switch to the next keyboard; work without full network access and without requiring Full Access; collect activity only to improve the keyboard. **Must not:** launch apps other than Settings, or repurpose keys (e.g. long-press Return to open the camera).
- 4.4.2 Safari extensions: run on current Safari; never interfere with system/Safari UI; no malicious or misleading code; request access to as few websites as necessary.

**4.5 Apple sites and services**
- 4.5.1 Apple RSS feeds OK; **no scraping Apple sites** or building rankings from them.
- 4.5.2 Apple Music (MusicKit): users must start playback and have standard controls; no charging for or indirectly monetizing Apple Music access; no downloading/uploading/sharing music files from MusicKit; MusicKit isn't a substitute for sync/adaptation licenses; cover art/metadata only for playback/playlists (not marketing without rights-holder permission); follow Apple Music Identity Guidelines; disclose access to Apple Music user data in the purpose string and don't share it, use it to identify users, or target ads.
- 4.5.3 Don't spam, phish or send unsolicited messages via Apple services (Game Center, push, Live Activities); never exploit Game Center Player IDs or aliases.
- 4.5.4 **Push notifications must not be required for the app to work**, must not carry sensitive personal/confidential info, and **must not be used for promotions/marketing unless users explicitly opt in via consent language in your UI, with an in-app way to opt out**.
- 4.5.5 Use Game Center Player IDs only as the terms allow; never display them in the app or to third parties.
- 4.5.6 Unicode that renders as Apple emoji is OK in the app and metadata; **don't embed Apple emoji images** in the binary or use them on other platforms.

**4.7 Mini apps, mini games, streaming games, chatbots, plug-ins, emulators** (HTML5/JS mini apps and games, streaming games, chatbots, plug-ins; retro console/PC emulators may download games) — you are responsible for all of it.
- 4.7.1 Must follow privacy rules (5.1), include **filtering, reporting with timely responses, and blocking** of abusive users, and use 3.1 payments for digital goods.
- 4.7.2 Don't expose native platform APIs to that software without Apple's permission.
- 4.7.3 Don't share data or privacy permissions with individual software without explicit consent each time.
- 4.7.4 Provide an index of the software and metadata with universal links to all of it.
- 4.7.5 Identify software above the app's age rating and restrict underage users by verified or declared age.

**4.8 Login services** — if a third-party/social login (Facebook, Google, X, LinkedIn, Amazon, WeChat…) sets up or authenticates the user's **primary account**, you must also offer an **equivalent login option** that: limits data to name and email; lets users keep their email private; and doesn't collect app interactions for advertising without consent. (Sign in with Apple meets this.) **Not required if:** you only use your own company's account system; you're an alternative marketplace using marketplace login; education/enterprise/business apps requiring existing org accounts; government/industry citizen ID or e-ID; or a client for a specific third-party service where users must sign in to that service to access their content.

**4.9 Apple Pay** — give all material purchase info before sale; use Apple Pay branding and UI correctly (marketing guidelines + HIG). **Recurring payments must disclose at minimum:** renewal term length and that it continues until cancelled; what's provided each period; actual charges; how to cancel.

**4.10 Monetizing built-in capabilities** — never charge for built-in hardware/OS capabilities (push notifications, camera, gyroscope) or Apple services (Apple Music access, iCloud storage, Screen Time APIs).

## 5. Legal
Comply with the law everywhere you distribute. Apps soliciting criminal or clearly reckless behavior are rejected; trafficking/child exploitation is reported to authorities.

**5.1 Privacy**

**5.1.1 Data collection and storage**
- (i) **Privacy policy link required in App Store Connect AND easily accessible inside the app.** It must state what data is collected, how, and all uses; confirm third parties (analytics, ad networks, SDKs, parent/affiliate entities) give equal protection; explain retention/deletion and how to revoke consent or request deletion.
- (ii) **Consent required for collecting user or usage data, even "anonymous" data.** Paid functionality must not depend on granting data access. Provide an easy way to withdraw consent. Purpose strings must clearly and completely describe data use. GDPR "legitimate interest" collection must fully comply with that law.
- (iii) **Data minimization:** request only data relevant to core functionality; prefer out-of-process pickers or the share sheet over full Photos/Contacts access.
- (iv) **Respect permission settings; never manipulate, trick or force consent** (e.g. don't require microphone access to upload photos). Offer alternatives when declined (manual address entry if Location is denied).
- (v) **Account sign-in:** if there are no significant account-based features, **allow use without login**. **If you support account creation, you must offer account deletion within the app.** Don't require personal info unless it's core to functionality or legally required. Unless your core function is tied to a specific social network, provide access without that network's login (basic profile import, sharing and inviting friends aren't "core"). Provide in-app revocation of social credentials and data access; never store social network tokens off-device; use them only to connect directly while the app is in use.
- (vi) Surreptitiously discovering passwords or private data → expulsion.
- (vii) **SafariViewController must be visible** (not hidden or obscured) and never used to track users without knowledge and consent.
- (viii) No compiling personal info from sources other than the user or without explicit consent (even public databases).
- (ix) Highly regulated fields (banking/finance, healthcare, gambling, legal cannabis, air travel, crypto exchanges) or apps needing sensitive info must be submitted by the **legal entity providing the service**, not an individual; cannabis sales apps geo-restricted to legal jurisdictions.
- (x) Basic contact info (name, email) may be requested only if **optional** and nothing depends on providing it (and kids rules apply).

**5.1.2 Data use and sharing**
- (i) No using, transmitting or sharing personal data without permission; disclose how and where data is used; **clearly disclose sharing with third parties, including third-party AI, and get explicit permission first**. Third-party sharing only to improve the app or serve ads (per the license agreement). **Tracking requires App Tracking Transparency permission.** **Never require enabling push, location or tracking to access functionality, content or rewards** (including gift cards/codes).
- (ii) No repurposing data without further consent.
- (iii) No covert profiling; never de-anonymize users or reconstruct profiles from Apple APIs or "anonymized/aggregated" data.
- (iv) Don't build contact databases from Contacts/Photos for yourself or to sell; don't collect which other apps are installed for analytics/ads.
- (v) Contact people from Contacts/Photos only at the user's explicit, individual initiative — **no "Select All" and no all-selected default**; show exactly how the message will look and who it will appear to come from.
- (vi) Data from HomeKit, HealthKit, Clinical Health Records, MovementDisorder, ClassKit, or depth/face mapping (ARKit, Camera, Photos) **may not be used for marketing, advertising or usage-based data mining**, including by third parties.
- (vii) Apple Pay data shared only to deliver goods/services.

**5.1.3 Health and health research**
- (i) Health/fitness/medical research data (Clinical Health Records, HealthKit, Motion & Fitness, MovementDisorder, human-subject research) **never for ads, marketing or data mining** — only for health management or research, with permission. Direct benefits to the user (e.g. insurance discount) OK if submitted by the benefit provider and not shared. Disclose the specific health data collected.
- (ii) **Never write false data into HealthKit; never store personal health info in iCloud.**
- (iii) Human-subject research needs informed consent (or a parent/guardian's for minors) covering: nature, purpose and duration; procedures, risks and benefits; confidentiality and data handling/sharing; contact for questions; withdrawal process.
- (iv) Independent ethics review board approval (proof on request).

**5.1.4 Kids**
- (a) Follow COPPA, GDPR and similar laws. Ask for birthdate and parental contact only to comply with those laws, and the app must still offer useful functionality regardless of age. Apps primarily for kids should avoid third-party analytics and advertising.
- (b) Limited exceptions follow 1.3. Kids Category apps, or any app that collects/shares minors' personal info (name, address, email, location, photos, videos, drawings, chat, persistent identifiers), need a privacy policy and full legal compliance. **A parental gate isn't the same as legal parental consent.**
- Non-Kids-Category apps can't imply children are the main audience anywhere in name, subtitle, icon, screenshots or description.

**5.1.5 Location services** — only when directly relevant to features; never for emergency services or autonomous control of vehicles/aircraft (small drones, toys and car-alarm remotes excepted); notify and get consent before collecting/using location; explain the purpose in-app (per HIG).

**5.2 Intellectual property** — only content you created or licensed.
- 5.2.1 No third-party trademarks, copyrighted works or patented ideas without permission; no misleading or copycat names/metadata; submit as the rights owner/licensee.
- 5.2.2 Using/monetizing/displaying third-party service content requires permission under their terms (proof on request).
- 5.2.3 **No downloading/saving/converting media from third-party sources** (Apple Music, YouTube, SoundCloud, Vimeo…) without explicit authorization; no illegal file sharing; check streaming terms.
- 5.2.4 Don't imply Apple supplies or endorses the app; "Editor's Choice" badges are applied by Apple only.
- 5.2.5 **Don't look confusingly similar to Apple products, interfaces (Finder), apps (App Store, Messages) or ad themes.** No Apple emoji in apps/extensions/keyboards/sticker packs. iTunes/Apple Music previews can't be used as entertainment (background music, game soundtrack) and must link to the music. Activity rings must not resemble the Activity control for Move/Exercise/Stand. Apple Weather data requires WeatherKit attribution.

**5.3 Gaming, gambling, lotteries** (heavily regulated; expect longer review)
- 5.3.1 Sweepstakes/contests must be sponsored by the app's developer.
- 5.3.2 Official rules shown in the app, stating **Apple isn't a sponsor or involved**.
- 5.3.3 **No IAP for credits/currency used in real-money gaming.**
- 5.3.4 Real-money gaming (sports betting, poker, casino, horse racing) and lotteries need licenses, **geo-restriction** to licensed locations, and must be **free** on the App Store. No illegal gambling aids (card counters). Lotteries need consideration, chance and a prize.

**5.4 VPN apps** — must use `NEVPNManager`; only developers enrolled as organizations; declare on an app screen, before purchase/use, what data is collected and how it's used; **never sell, use or disclose data to third parties** (commit in privacy policy); obey local law and provide license info where required. Approved parental control, content blocking and security apps may also use the API.

**5.5 Mobile Device Management** — capability must be requested; only commercial enterprises, educational institutions, government agencies (and limited parental-control/security cases); same up-front data declaration and no-sharing commitment as VPN; third-party analytics only about the MDM app's performance. Configuration profile apps follow the same rules.

**5.6 Developer Code of Conduct**
- Treat everyone with respect (reviews, support, App Store Connect); no harassment, discrimination, intimidation or bullying. Repeated manipulation/fraud → expulsion.
- **Never prey on or rip off customers:** no tricking into unwanted purchases, forcing unnecessary data sharing, sneaky price increases, charging for undelivered features/content, or other manipulative practices.
- Terminated accounts may be restored after an approved written improvement plan.
- 5.6.1 Respond to reviews respectfully and on-topic — no personal info, spam or marketing. **Use the system API to prompt for reviews; custom review prompts are disallowed.**
- 5.6.2 Accurate, truthful, current developer identity and contact info.
- 5.6.3 **No discovery fraud** — never manipulate charts, search, reviews or referrals.
- 5.6.4 Maintain quality; excessive complaints, negative reviews or refund requests can indicate a Code of Conduct problem.

## After You Submit
- **Timing:** complex or novel apps take longer; repeated rejections for the same issue or manipulation slow review.
- **Status:** tracked in App Store Connect.
- **Expedited review:** only for genuinely critical timing; abuse gets requests refused.
- **Release date:** future-dated apps appear only on that date; allow **up to 24 hours** to show in all storefronts.
- **Rejections:** reply to App Review through App Store Connect with questions or extra info.
- **Appeals:** submit to the App Review Board; you can also suggest guideline changes.
- **Bug-fix submissions:** for apps already live, bug fixes aren't held for guideline violations (except legal or safety issues) — accept the offer in App Store Connect and fix the issue in the next submission.

Source last updated (per Apple): October 16, 2026.

---
# Linked App Review help pages

## Provide information for a complete review
Source: https://developer.apple.com/help/app-review/before-submitting-for-review/complete-review

Incomplete submissions are rejected. In App Store Connect › App Review Information, include:
- **About the app:** concept and business model (new apps) or what changed and where to find it (updates); purpose and audience; **devices and OS versions tested**; external services used for core functionality (data providers, auth, payments, **AI services**); for required hardware, a **video of the app running on a real device** pairing with it (not a screen recording); regional differences (or confirm none).
- **Demo accounts:** working credentials at submission time (expired ones cause rejection); credentials for every account type (admin vs. user) in Notes; **an account with an expired subscription** for apps with auto-renewable subscriptions so the full purchase flow can be reviewed; any required authentication code in advance (otherwise a call may be needed — typically 3–5 business days).
- **Demo mode** instead of an account for sensitive/regulated apps — must show full features with demo data.
- **Regulated documentation** (per country/region where distributed):

| Guideline | Typical documentation |
|---|---|
| 1.4.1 Medical diagnosis/treatment | FDA, CE or CFDA clearance, or test report / peer-reviewed study |
| 1.4.3 Cannabis | Dispensary license |
| 1.7 Crime reporting | Law enforcement/government partnership on official letterhead |
| 2.1 Registration | ISBN or GRN (China) |
| 3.1.5 Crypto | Exchange license, partner docs, legal opinion |
| 3.2.1 Financial apps | Partnership with the licensed institution |
| 3.2.1/3.2.2 Loans | Loan and business licenses, lender agreement |
| 4.1 / 5.2.1 / 5.2.3 Third-party IP, fan apps, sports, music/video | Signed contracts, emails, licenses |
| 5.0 Published works in China | Publication/internet publishing permits |
| 5.1.1 Seller/company verification | Partnership evidence (insurer, broker, government) |
| 5.1.3 Health research | Ethics board/IRB approval, consent form |
| 5.3.3 Lotteries/raffles | Gambling license; SUSEP/SECAP (Brazil); lottery license (China) |
| 5.3.4 Gambling | Gambling license |

- Unsure? Request a one-on-one App Review appointment before submitting.

## Test your app on compatible devices
Source: https://developer.apple.com/help/app-review/before-submitting-for-review/test-compatible-devices

- Review happens on **real devices on real networks** — test every platform where the app can run, not just simulators.
- TestFlight: up to **100 internal** and **10,000 external** testers; the first external build is reviewed.
- **iPhone apps run on iPad in compatibility mode** (unless they depend on iPhone-only capabilities), and compatible iPhone/iPad apps run unmodified on Apple silicon Macs and Apple Vision Pro. **Removing iPad as a supported destination in Xcode does not stop iPad distribution** — test compatibility modes.
- Build adaptive UIs for all screen sizes, orientations and inputs; never crash when optional hardware is missing.
- Restrict devices only for genuine hardware dependencies with `UIRequiredDeviceCapabilities` (not as a distribution preference). Camera/navigation apps may not suit visionOS; touch-heavy apps may not suit Mac.

## Configure In-App Purchases for review
Source: https://developer.apple.com/help/app-review/before-submitting-for-review/configure-in-app-purchases

- Review uses the **sandbox**. The Account Holder must accept the **Paid Apps Agreement** (paid IAPs won't work in review otherwise).
- Create a Sandbox Apple Account; configure products in App Store Connect; fetch product info via StoreKit before showing it so UI matches configuration; test in sandbox first.
- Note storefront/device restrictions on IAPs in review notes; submit IAPs once "Ready for Review". (IAPs don't need prior approval to work in review.)

## App Store Improvements (removal of outdated apps)
Source: https://developer.apple.com/help/app-review/safe-and-trusted-store/app-store-improvements

- Apple continually removes apps that don't function, don't follow current guidelines, or are outdated.
- Apps **not updated in 3 years** with near-zero downloads in a rolling 12 months get notice and **90 days** to update, or are removed (re-submittable anytime). **Apps that crash on launch are removed immediately.** Removed apps keep their name and keep working for existing users.

## Guideline 2.3.3 — Screenshots
Source: https://developer.apple.com/help/app-review/guideline-reference/2-3-3-screenshots

- **More than half of the screenshots for each device must show the app in use** (3 screenshots → at least 2; 4 → at least 3). The rest may be marketing or benefit slides.
- Do: show main features; update with every version; show configurations like Dark Mode; overlays to show input (touch, Pencil); show extended functionality or other Apple platforms when part of the experience; one image may span several screenshots.
- Don't: only login/splash screens; misrepresent the UI; let overlays crowd out the app; show hardware or an overlay with no app UI.
- Screenshot counts can differ per device (one in-use screenshot is enough); localizations can differ but are judged the same way. Third-party platform references (e.g. in a status bar) fall under 2.3.10.

## Guideline 4.1 — Preventing copycat rejections
Source: https://developer.apple.com/help/app-review/guideline-reference/4-1-prevent-copycat-rejection

- Repeated copycats or impersonation → account closure. Build distinct concepts, designs and features.
- Don't imitate other apps' features, functionality, look or feel; don't use protected material or popular app names/trademarks in any metadata field.
- Keep developer/company name and Support URL accurate; never submit fraudulent documentation (→ removal).

## Guideline 5.1.1(ii) — Purpose strings
Source: https://developer.apple.com/help/app-review/guideline-reference/5-1-1-purpose-strings

- Name the specific feature or outcome; one purpose string per protected resource; give a concrete example; **one brief, complete sentence, active voice, sentence case, ending with a period**; no marketing copy or feature lists.
- Rejected styles: "To use location." / "Your data will be used to provide a better experience." Good: "The app uses location data to determine the recommended route to your destination and provide turn-by-turn directions."
- **Localize purpose strings** for every supported language.
- **You're responsible for third-party SDK permission requests** — add accurate purpose strings or remove the unused API references from the binary.

## Guideline 5.1.1(v) — Account deletion
Source: https://developer.apple.com/help/app-review/guideline-reference/5-1-1-account-deletion

- Easy to find (usually account settings). Must delete the **entire account and associated personal data** — deactivation alone is insufficient.
- If deletion finishes on a website, **link directly to that page**.
- Say how long it takes and confirm when done; explain IAP billing/cancellation; disclose any legally retained data.
- Customer-service flows (calls, email, chat) are allowed only for highly regulated industries (5.1.1(ix)).
- Re-authentication or confirmation codes are fine, but unnecessarily hard deletion fails review.
- Sign in with Apple: revoke tokens via the REST API; handle server-to-server notifications.
- Required even if account creation happens on the web (and linking out to a browser for sign-up is a poor experience under Guideline 4) and for **auto-created "guest" accounts**.
- Manual/slow deletion OK if you state the timeline and confirm completion.
- **User-generated content shared with others (photos, videos, posts, reviews) must be deleted too.**
- Must be available to **everyone worldwide**, not just CCPA/GDPR regions.
- Subscribers: tell them Apple billing continues and ask them to cancel first (`showManageSubscriptions` or https://apps.apple.com/account/subscriptions/); refunds via `beginRefundRequest`; scheduled deletion at expiry is OK only alongside an immediate option.

## Kids and age-appropriate experiences
Source: https://developer.apple.com/app-store/kids-apps/

- **Age ratings:** 4+, 9+, 13+, 16+, 18+ — calculated from the App Store Connect questionnaire (sensitive content frequency, parental controls, messaging, advertising, UGC, social media capabilities); you may choose a higher rating; check regional rules.
- **Kids Category:** pick an age band — **5 and under, 6–8, or 9–11**; follow 1.3 and 5.1.4; no personal or device info to third parties (even in adult sections) without explicit parental consent; ads must be human-reviewed for age appropriateness; **parental gates** (adult-level tasks) before purchases or links out (web, social, other apps) — voice prompts help pre-literate kids.
- Tools: **Declared Age Range API** (age range shared by parents; Always/Ask First/Never; no birthdate; in some regions also age category and assurance method), **PermissionKit** (kids ask parents to chat/follow/add contacts; one-tap approval in Messages), **Significant Change API** (parental consent for significant app changes under age assurance laws), **SensitiveContentAnalysis** (detect nudity and violent media before display, including live video calls), Screen Time/DeviceActivity/ManagedSettings/FamilyControls for parental controls, media ratings, StoreKit **Ask to Buy** and `ageRatingCode`, App Store Server Notifications when parents withdraw consent.
- Time Allowances: Entertainment/Games categories and social-media-capable apps are grouped for parental time limits; social features add a Social Media content descriptor.
