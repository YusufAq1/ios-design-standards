# Technologies

Summarized from Apple's Human Interface Guidelines (iOS and iPadOS guidance only). Paraphrased; exact specs kept. Open the source link for Apple's exact wording. Many of these pages include trademark/branding rules — follow them exactly when you show Apple marks.
Overview: https://developer.apple.com/design/human-interface-guidelines/technologies

## AirPlay
Source: https://developer.apple.com/design/human-interface-guidelines/airplay

- Prefer the system player (`AVPlayerViewController`) — includes AirPlay, chapters, subtitles, captions.
- HLS playlists must include the full range of resolutions (720p that looks fine on iPhone looks bad on a 4K TV).
- Stream only content people expect (not background loops or short in-app videos).
- Support both streaming and mirroring; support remote control events (Lock Screen, Siri, HomePod).
- Keep playing when the app backgrounds or the device locks; never start mirroring automatically.
- Don't interrupt other apps' playback unless starting immersive content (autoplay/inline video stays local).
- Keep the app usable during AirPlay; don't let other in-app videos start and interrupt the stream.
- Custom players: buttons that match system appearance and states (starting, playing, unavailable); **Apple-provided AirPlay symbols only**; AirPlay icon in the **lower-right corner** (iOS/iPadOS 16+).
- **Icon usage:** black on light backgrounds, white on dark, or a custom color — matching other technology icons; place it consistently with them. Never use the AirPlay icon or name in custom interactive elements (only non-interactively). Name beside or below the icon in your layout font; don't put the icon inside text or substitute it for the word. Keep AirPlay less prominent than your app.
- **Naming:** "AirPlay" (capital A and P; all caps only if the layout is all caps). Always a noun: "Use AirPlay to listen on your speaker" — never "AirPlay to your speaker". Use "works with/supports/compatible with" ("[App] is compatible with AirPlay"), not "[App] has AirPlay". "Apple AirPlay" is fine.

## Always On
Source: https://developer.apple.com/design/human-interface-guidelines/always-on

**iPhone** (14 Pro and later) shows Lock Screen widgets and Live Activities dimmed when set face-up. (Not iPadOS.)
- Redact sensitive info (balances, health data), including in notifications.
- Keep useful personal info glanceable when appropriate (flight arrival, ride arriving).
- Keep key content legible; dim secondary text, images and fills; replace rich images/large color areas with dimmed colors.
- Keep the layout stable: show interactive components as unavailable rather than removing them; make infrequent, subtle updates (score changes only, not play-by-play) — motion is very visible on a phone lying face up.
- Ease motion to rest; never stop it abruptly.

## App Clips
Source: https://developer.apple.com/design/human-interface-guidelines/app-clips

Lightweight, instantly available slice of the app (task-in-the-moment or demo). Launched from App Clip Codes (best), NFC tags, QR codes, Maps, Siri Suggestions, Smart App Banners, Safari App Clip cards, Messages links and other apps (iOS 17+). iOS and iPadOS only.

**Design**
- Let people finish the task or full demo inside the clip — never require the full app to complete it.
- Essential features only; advanced features stay in the app.
- **Not just marketing; no ads.**
- **No web views** — if you only have web content, link to the website instead.
- Linear, focused UI: no tab bars, complex navigation or settings; minimal screens and forms.
- Launch straight into the relevant part; include all assets; **no splash screen**; no waiting.
- Keep it small; avoid downloading extra data.
- Make it shareable via links to specific points.
- Use Apple Pay for payment; avoid requiring an account (or ask after the task; use Sign in with Apple).
- When the full app replaces the clip, keep the experience familiar — don't make people sign in again.

**Privacy:** no background operations; store minimal data securely; don't rely on previously stored data (clips are deleted); keep logins off-device; offer Sign in with Apple and Apple Pay.

**Promoting the app:** the system card and banner already link to the App Store. Don't degrade the experience asking for install; recommend the app (`SKOverlay`) only after a task or natural pause, politely, not repeatedly, not via push notifications.

**Notifications:** may be scheduled for up to **8 hours** after launch; ask for longer permission only if truly needed (e.g. car return reminder); task-related only, never promotional.

**Platform providers (many businesses):** show the business's branding, not yours; handle multiple businesses/locations (switching, location verification).

**App Clip card:** informative image (photo/graphic, not a screenshot), **no text in the image**, **1800×1200 px PNG or JPEG, no transparency**. Title **≤30 characters**, subtitle **≤56 characters**. Action verb: **View** (media/info), **Play** (games), **Open** (everything else).

**App Clip Codes:** always use Apple-generated codes (App Store Connect or the generator tool) — never modify (no filters, glows, shadows, gradients, reflections; keep aspect ratio; scale all strokes). Badge with App Clip logo when space allows; use the logo-free version if clear space is lacking or on disposable items or items tied to gambling/drinking; never use the logo alone.
- NFC-integrated (iPhone glyph) where people can touch it; scan-only (camera glyph) for posters, out-of-reach signs and digital use.
- Flat or cylindrical surfaces only (code width ≤ 1/6 of circumference); rigid, not deformable; good light; not at steep angles; unobstructed (no overlays, animation or dimming); upright.
- **Minimum sizes:** print **3/4 in (1.9 cm)** diameter; digital **256×256 px** PNG/SVG; NFC tag **≥35 mm** (code ≥1.37 in / 3.48 cm). Distance-to-size ratio no more than **20:1** (ideally **10:1**). At least as large as any adjacent QR code. Clear space = the gap between center glyph and the code ring.
- Call to action: "Scan to [do X]" / "Hold your iPhone near the [object] to…". Title case "App Clip", "App Clip Code"; follow Apple trademark rules; never translate Apple trademarks.
- **Printing:** test scans from many angles; matte, non-textured materials (no gloss/holographic/thin laminate; matte laminate if needed); UV-resistant outdoors; flexographic (pro) or inkjet (desktop); rasterize SVG at ≥600 ppi, print ≥300 dpi; convert sRGB → CMYK with relative colorimetric intent (Generic CMYK or GRACoL 2013; ΔE ≤2.5); grayscale printers → generate grayscale codes; **Type 5 NFC tags**; test print runs and track SVG ↔ URL mapping; use Apple's calibration test sheets.
- **Legal:** only Apple-generated codes; stop displaying codes for inactive clips; never use the code or marks in your company/product name; don't register them; don't add symbols.

## Apple In-App Purchase
Source: https://developer.apple.com/design/human-interface-guidelines/apple-in-app-purchase

**IAP is for digital goods** (premium content, subscriptions). **Apple Pay is for physical goods, real-world services and donations.** Types: consumable, non-consumable, auto-renewable subscription, non-renewing subscription. (Advanced Commerce API for huge multi-creator catalogs.)

**Best practices**
- Let people experience the app before buying; consider limited free access.
- Integrate the store into your app's own style.
- Short product names that don't truncate; plain descriptions.
- **Always show the total billing price** for every purchase.
- Hide the store (or explain) when payments aren't allowed (`canMakePayments`).
- **Never modify or imitate the system confirmation sheet.**

**Family Sharing** (up to five family members): mention it prominently ("Family", "Shareable" in names; sign-up screen); explain benefits; word messages for both purchaser and members ("Your family subscription includes…").

**Purchase help and refunds**
- Offer a help screen before refund: missing-purchase help, FAQs, contact/feedback, plus a link into the system refund flow (`beginRefundRequest`).
- Title it simply: "Refund" or "Request a Refund".
- Show recent purchases with image, name, description, purchase date.
- Offer alternatives (immediate fulfillment, a make-good item) but **never block the refund** — the button must be visible without scrolling or another screen.
- Never characterize Apple's refund policy or predict outcomes; you may link to Apple's refund page.

**Auto-renewable subscriptions**
- Show subscription value during onboarding with a clear call to action and terms.
- Offer a range of content, levels and durations; consider freemium, metered paywall or free trial.
- Prompt at relevant moments (near free limit) and keep subscribe entry points available.
- Never push a subscription on existing subscribers; offer sign-in for subscriptions bought elsewhere.

**Sign-up screen must include:** clear, distinct option names with **price and duration**; for intro offers the intro price, its duration and the standard price afterward; subscription name, duration and what's provided each period; **localized billing amount**; a **sign in / Restore Purchases** option; links to **Terms of Service and Privacy Policy** (also in App Store metadata). Make the billed total the most prominent number (per-month breakdowns subordinate). Free trials must state duration and the amount charged when the trial ends. Ask only for essential info at sign-up. Put a subscribe option in settings too.

**Offer codes (iOS/iPadOS):** one-time codes (App Store Connect; redeem via URL, in app, or App Store) or custom codes (e.g. NEWYEAR; URL or in app only — tell people how to redeem). Custom codes: **alphanumeric ASCII only**. Describe offers clearly. Support in-app redemption with a "Redeem Code" button (paywall, onboarding, settings) that opens the system sheet. Optional promotional image (defaults to app icon). Welcome people right after redemption, even before first launch.

**Managing subscriptions**
- Show subscription summaries with the next renewal date in settings/account.
- Consider the system management UI (`showManageSubscriptions`).
- Retention offers on cancel (remind what they lose, another plan, discount) and win-back offers later are fine.
- **Cancelling must always be easy** — never buried or disguised.

## Apple Pay
Source: https://developer.apple.com/design/human-interface-guidelines/apple-pay

**Use for:** physical goods, real-world services (memberships, hotels, tickets), donations, and recurring payments. Digital goods → In-App Purchase. People authorize with Face ID / Touch ID.

**Offering Apple Pay**
- Offer it wherever supported; hide it where the device can't use it.
- If you check for an active Wallet card, **Apple Pay must be the primary (not necessarily only) option** everywhere you check — e.g. preselected; never in a separate step/flow.
- Apple Pay buttons only start payment (or Apple Pay setup). Custom payment buttons must **not** show "Apple Pay" or the logo — then show the Apple Pay mark or mention Apple Pay in text on the same page.
- The **Apple Pay mark** only signals acceptance — never a button.
- Never hide or disable the Apple Pay button; if something's missing (size, color), explain after tap.

**Checkout**
- Keep checkout inside your branded flow; no new pages/windows.
- Assume people want Apple Pay: show it first, larger, or separated by a line.
- Apple Pay buttons on product pages buy **that single item only** (exclude cart; remove it from the cart afterward). Express checkout buys the whole cart with one shipping method/address.
- Allow coupon/promo codes on the payment sheet (especially express); show any applied code.
- Collect required options (size, color) before the button; on missing info, highlight and jump to the field.
- Collect optional info (gift notes, delivery instructions) before or after — the sheet can't.
- Multiple shipping methods/addresses per item and in-store pickup location: collect before the sheet; show pickup address read-only.
- Prefer Apple Pay's contact/shipping data even if you have stored data.
- **Don't require an account before purchase**; offer registration on the confirmation page, prefilled.
- Report results in the sheet with fixable error messages; then show an order confirmation/thank-you page (if you mention Apple Pay: "1234 (Apple Pay)" or "Paid with Apple Pay").

**Payment sheet**
- Request only essential info (no shipping address for an e-gift card).
- Shipping options: description, cost, optional delivery/pickup date range (time-zone aware); pickup windows.
- **Line items** for extra charges, discounts, pending costs, add-on donations, recurring and future payments — **not** an itemized product list. Keep them short, one line.
- Total line: "Pay [Business Name]" matching the bank statement; marketplaces: "Pay [End Merchant] (via [Your Business])".
- Disclose possible later charges (ride price, tips) with an **Amount Pending** subtotal where allowed; reflect preauthorization amounts accurately.
- Don't add your own spinners — the sheet shows progress.
- Websites: provide a **60×60 pt** icon (120×120 px @2x, 180×180 px @3x).

**Errors**
- Validate before authorization where possible (only card type and redacted address are available beforehand).
- Be forgiving: ignore ZIP+4 extras, accept phone numbers in any format.
- Report the correct status code with a custom message (`PKPaymentError`).
- Messages: specific field and expectation ("Zip code doesn't match city", "Shipping not available for this state"); noun phrases, sentence case, no ending punctuation, **≤128 characters**.
- On cancellation/timeout, cancel the in-progress payment; people restart via the button.

**Subscriptions / recurring:** explain frequency and terms before the sheet; line items for frequency, discounts, upfront fees (and when billing starts if nothing is due now); trial line items with trial amount (even $0), regular amount and start date; total shows what's charged now; show the sheet on changes only if the cost increases; billing-agreement field is a short plain summary or left blank.

**Donations** (approved nonprofits): a "Donation $50.00" line item; preset amounts ($25/$50/$100) plus Other Amount.

**Buttons**
- **Always use Apple's API** (`PKPaymentButton`) — never custom designs or images. Gives localized captions, scaling, VoiceOver, adjustable corner radius.
- Types: Buy, Pay (bills), Check Out, Continue, Book, Donate, Subscribe, Reload, Add Money, Top Up, Order, Rent, Support, Contribute, Tip, plain Apple Pay; plus **Set Up Apple Pay** (in Settings, profile, or interstitial).
- Styles: automatic (preferred); black (light backgrounds); white with outline (light backgrounds lacking contrast); white (dark backgrounds).
- At least as large as other payment buttons; visible without scrolling. **Right of** Add to Cart side by side; **above** it when stacked. Match corner radius to your buttons.
- **Minimums:** plain Apple Pay button **100×30 pt**; Book/Buy/Check Out/Donate/Set Up/Subscribe with Apple Pay **140×30 pt**; margins **1/10 of button height**. Too small for the localized title → system falls back to the plain button (no fallback for Set Up).
- **Mark:** Apple artwork only; change height only (≥ other payment marks); no width/radius/aspect changes, no ™ or extra content, keep the border, no effects, no flip/rotate/animate; clear space **1/10 of height**; don't share a border with other graphics.

**Naming:** "Apple Pay" — two words, capital A and P; never plural/possessive; never the Apple logo in place of "Apple"; in the US, ® on first body-text mention (not in checkout option labels); match your own font; never translate. Text-only "Apple Pay" in payment selection only if all options are text-only; otherwise use the mark.

## Augmented reality
Source: https://developer.apple.com/design/human-interface-guidelines/augmented-reality

ARKit on iOS/iPadOS (camera passthrough with virtual 3D objects).
- AR-only apps should be limited to ARKit-capable devices; optional AR features are simply hidden on unsupported devices (no error).
- Use the full display; avoid cluttering controls.
- Realistic objects: detailed assets, correct scale on detected surfaces, environment lighting, camera grain, soft top-down shadows, update at **60 fps** to avoid jumps/flicker. Prefer small/coarse reflective surfaces (reflections are approximations).
- Audio and haptics to confirm contact; minimal text in the scene.
- Extra info/controls in screen space; persistent controls as indirect 2D controls reachable without regripping, optionally translucent (Measure app).
- Expect cramped spaces and missing flat surfaces — state requirements up front; offer alternatives.
- Comfort: avoid long arm-extended holds; short game levels with breaks; introduce movement gradually; avoid encouraging large or sudden movements (safety).

**Coaching:** use the system coaching view (`ARCoachingOverlayView`) for initialization and relocalization; hide unrelated UI meanwhile; custom coaching should mirror it.

**Placement:** show a surface-aligned indicator when placement is possible; place instantly and refine later (nudge back onto the surface); guide to offscreen objects with edge indicators/sound; don't align precisely to surface edges (approximate); use plane classification (furniture only on "floor", board games on "table").

**Interaction:** prefer direct manipulation (indirect controls when people move around); standard gestures (one-finger drag to move, two-finger rotate); treat touches near an object as targeting it; allow scaling only when it makes sense (not for real products like a chair) and never to fake distance; test similar gestures (pinch vs rotate); movement obeys surface physics without jumping or vanishing; consider proximity/motion responses (a character looks at you).

**Multiuser:** consider people occlusion; let newcomers join via implicit map merging.

**Image/object detection:** keep attached content up to **1 second** after a detected image disappears before fading; **≤100 reference images** active at once (swap by context); limit images requiring tracked positions.

**Language:** no jargon ("ARKit", "tracking", "plane"). E.g. "Unable to find a surface. Try moving to the side or repositioning your phone." / "Tap a location to place the [object]." / "Try turning on more lights and moving around." / "Try moving your phone more slowly." Prefer 3D hints (rotation indicator around an object) over text overlays. Critical text in screen space; 3D text faces the viewer at constant size. Tap-for-more indicators fit the experience.

**Interruptions:** use coaching for relocalization; consider hiding objects until repositioned; embed non-AR tasks inside AR to avoid exits (change upholstery in place); allow cancelling relocalization (Reset button); indicate face-tracking loss after about **0.5 s**.

**Problems:** always offer reset; suggest fixes in friendly language (more light, move slower, point at a textured surface).

**AR glyph and badges:** glyph only for launching ARKit experiences; change only size/color; clear space **10% of height**. AR badges (collapsed/expanded) only to mark items viewable in ARKit AR, unaltered; prefer the full badge (glyph-only for tight spaces); use only when some items aren't AR-viewable; same corner every time; clear space **10% of height**.

## CareKit
Source: https://developer.apple.com/design/human-interface-guidelines/carekit

Care plan apps (chronic illness, recovery, wellness). CareKit UI (views) + CareKit Store (on-device database).
- **Privacy:** a clear privacy policy URL is required at submission; get permission for any system data and protect all data.
- **HealthKit:** request access only when needed, in context (ask for weight when logging weight), and re-request when needed; add a clear purpose message to the **system** permission screen — no custom look-alike screens; manage sharing only through system Settings › Privacy (no in-app data-flow screens).
- Motion data, photos (e.g. injury progress photos for care teams) and ResearchKit (surveys, consent) only with permission.

**Views** — use each category for its purpose: **tasks** (meds, therapy, symptom logging), **charts** (treatment progress), **contacts** (call, message, email, map). Header (text, symbol, disclosure, separator) + content stack.
- Task info: title (required, e.g. "Ibuprofen"), schedule (required, "Four times a day"), instructions, group ID.
- Task styles: *simple* (one step), *instructions* (one step + text like "Take on an empty stomach"), *log* (timestamped events like nausea), *checklist* (multistep with descriptions), *grid* (compact multistep buttons; custom UI allowed).
- Color can reinforce categories (meds vs. activity) but never alone. Describe accurately and briefly (marketing drug names; skip redundant "take"). Add videos/images for complex steps.
- Charts (bar, scatter, line): highlight trends (meds vs. pain); short labels (units in axis, e.g. BPM); distinct, high-contrast colors (not shades of one color); legends when needed; clear time units; consolidate large datasets; offset data so small values stay readable.
- Contacts (simple/detailed): color can categorize care team members.
- **Notifications:** minimize; coalesce multiple items; offer a detail view to complete tasks without opening the app.
- **Symbols/branding:** prefer CareKit's built-in symbols; in grids use SF Symbols (pill, figure walking); custom symbols relate to health — never decorative or corporate logos; subtle branding, no advertising.

## CarPlay
Source: https://developer.apple.com/design/human-interface-guidelines/carplay

**iOS only** (iPhone drives the car display). Built from system templates (audio, communication, navigation…). Drivers need fast, minimal interaction.
- No interactions on iPhone while CarPlay is active; do setup before driving. Never block CarPlay waiting for iPhone input; everything must work with iPhone **locked** and out of reach.
- **Audio:** don't autoplay (unless single-source or resuming); don't start an audio session until ready (it silences the radio); start as soon as buffered; show Now Playing immediately and load metadata after; resume only after resumable interruptions (calls) if audio was playing; adjust relative levels only, never master volume.
- **Layout:** common displays 800×480 (5:3), 960×540 and 1280×720 (16:9), 1920×720 (8:3) — system scales. Clean, scannable, high-value info; consistent look; primary content large and in the **upper half**.
- **Color:** limited palette matching your logo; don't share colors between interactive and non-interactive elements; test in a real car in varied light; support light and dark; inclusive color.
- **Icons/images:** supply @2x and @3x; mirror the iPhone app icon; **no black icon background** (lighten or add a border). CarPlay icon **120×120 px @2x, 180×180 px @3x**.
- **Errors:** report only when necessary and in CarPlay — never tell drivers to pick up their iPhone.

## Game Center
Source: https://developer.apple.com/design/human-interface-guidelines/game-center

Apple's social gaming network (GameKit): friend discovery, invites, activity across the system, discovery in Top Played and recommendations.
- Check sign-in at launch and initialize the player then (best experience and discovery).
- **Access point** (opens the Game Overlay on iOS/iPadOS): show in menus or settings — **not during gameplay**, splash screens, cinematics or tutorials; choose a fixed corner and keep controls clear of both collapsed and expanded states; consider pausing while the overlay is open.
- Custom links into the overlay (leaderboards, profile) use Apple's official artwork, unaltered.
- Terminology: **Game Center** (not GameKit/GameCenter), **Game Center Profile** (not Account/Player Info), **Achievements** (not Trophies/Medals), **Leaderboards** (not Rankings/Scores), **Challenges** (not Competitions), **Add Friends**. Use system translations of "Game Center".

**Achievements**
- Map to the four states: locked, in-progress, hidden, completed.
- Upload order = display order (follow the common path through the game).
- Title and description **max two lines each**; title case for titles, sentence case for descriptions.
- Use progressive achievements so the system shows encouraging progress messages.
- Unique, high-quality image per achievement (placeholder otherwise); keep content centered — circular mask. **512×512 pt (1024×1024 px @2x)**, PNG/TIF/JPG, sRGB or P3, ≥72 DPI.

**Leaderboards**
- Classic (all-time best, never ends) or recurring (resets daily/weekly for more chances to lead).
- Use leaderboard sets to group by difficulty, activity or theme.
- Unique image per leaderboard: **512×512 pt (1024×1024 px @2x)**, cropped area **512×312 pt (1024×624 px @2x)** in sets — keep key content inside; JPEG/PNG, sRGB or P3, ≥72 DPI.

**Challenges** (time-limited competitions built on leaderboards)
- Short skill-based activities of **1–5 minutes**, playable solo (fastest lap, most enemies, daily puzzle).
- Track the **most recent** score per attempt, not personal bests or overall progress (fairness).
- Deep-link straight to the challenge's mode/level; route first-timers through needed onboarding first and tell them the challenge follows.
- Artwork **1920×1080 pt (3840×2160 px @2x)**, crop-safe area **1465×767 pt (2930×1534 px @2x)**; keep primary content clear of title/description; localize any text.

**Multiplayer** (real-time and turn-based)
- Party codes (about 8 characters, e.g. "2MP4-9CMF"): allow late join, leaving and returning; show the current code in-game; allow manual code entry.
- Support matchmaking through the overlay or custom UI (nearby, recent, friends, contacts).
- Activity artwork: same size as challenges (1920×1080 pt; crop area 1465×767 pt).

## Generative AI
Source: https://developer.apple.com/design/human-interface-guidelines/generative-ai

**Principles**
- Design responsibly: outputs vary even for identical inputs — design for robustness, inclusion, care and privacy.
- Keep people in control: honor clear in-scope requests; let them dismiss, revert or retry; clearly label where AI is used.
- Be inclusive: ask for needed personal attributes instead of inferring them (especially when depicting people); avoid stereotype-prone assumptions (gender, relationships); test with diverse people.
- Use generative features only where they add clear value (time saved, communication, creativity).
- Work well when AI is unavailable or declined — offer non-AI fallbacks where possible (Genmoji vs. regular emoji).

**Transparency:** say when and where AI is used; **never pass AI off as human**; follow regional disclosure laws. Set expectations about capabilities and limits (short tutorial, curated starter suggestions, explain known weaknesses).

**Privacy:** choose on-device models where they suffice (private, fast, offline); for server models, minimize what's sent, process locally first, and tell people what's sent, stored and used for training. Ask permission before using personal data or usage data; use the minimum; allow opt-out; explicit permission for training/storage; vet third parties; outputs may leak sensitive info; stricter rules for kids' apps. Explain data use concisely and specifically.

**Models and data:** evaluate model capabilities early; some models are unavailable on some devices/conditions (Foundation Models needs a compatible device with Apple Intelligence on). Use diverse, properly licensed datasets; test for bias and misinformation.

**Inputs**
- Guide people with diverse example inputs.
- Reduce and disclose **hallucination** risk: state that AI content may contain errors; scope requests narrowly; avoid requesting facts the model can't verify; don't use AI output where errors could harm.
- **Never automate destructive or irreversible actions** (deleting photos, purchases) — confirm significant actions; follow model usage policies and local AI regulations.

**Outputs**
- Put Edit, Undo, Retry, Adjust next to generated content; confirm when corrections take effect.
- When blocked, coach people toward better requests ("Unable to use that description" + example prompts).
- Test misuse: out-of-scope, vague, sensitive, controversial and adversarial prompts; write policies and iterate.
- Avoid reproducing copyrighted content (use protected base models, curated/pre-approved prompts, explicit instructions).
- Design for latency: loading states or background generation.
- Specific progress messages ("Summarizing key themes from your notes", not "Processing…"); plain-language errors with a next step.
- Consider offering several meaningfully different results to choose from.

**Continuous improvement:** update models, block lists and prompts; retest every model change; voluntary, unobtrusive feedback (thumbs up/down plus detailed option); decouple model from UX so it can be swapped.

## HealthKit
Source: https://developer.apple.com/design/human-interface-guidelines/healthkit

- **Don't request health data unless the app has real health/fitness functionality.**
- Privacy policy URL required at submission; protect data; show how it's used.
- Request access only when needed and in context (on logging weight), and request every time access is needed (permissions can change).
- Explain why on the **system** permission screen — no custom look-alike screens.
- Manage sharing only via system Settings › Privacy — no in-app screens that change data flow.
- **Activity rings:** same rules as the Activity rings component (Move/Exercise/Stand only, one person, not decoration or branding, unaltered colors and background, margins, separate from other rings, no rings in notifications) — `HKActivityRingView`.
- **Apple Health icon:** Apple-provided only; show the name "Apple Health" nearby; no smaller than other health app icons in the same view; **never a button**; no masking, borders, overlays, gradients, shadows or effects; clear space **1/10 of its height**; not composited on other graphics; not inside text or as a word substitute. **No Health app screenshots.**
- **Wording:** say "Apple Health" or "the Apple Health app" — **never "HealthKit"** in user-facing text ("works with the Apple Health app"). Capitalize as two words; use the system translation of "Health".

## HomeKit
Source: https://developer.apple.com/design/human-interface-guidelines/homekit

Integrate with the Apple Home app to set up, name, organize, control and automate accessories.

**Model and vocabulary** (use HomeKit's terms in UI): home → rooms, zones (e.g. upstairs) → accessories (category: light, fan…) → services (controllable features; call them by descriptive names like "ceiling fan light", never "service") → characteristics (speed, brightness; never "characteristic"); service groups ("reading lamps"); actions; **scenes** (always "scene" in UI, never "action set"); automations.
- Reference the hierarchy even if your UI is organized differently; show room/zone/home info in accessory detail views; support multiple homes; never duplicate Home app settings — defer to them.

**Setup**
- Use the system setup flow (`performAccessorySetup`), then a custom post-setup for unique features.
- Purpose string e.g. "Lets you control this accessory with the Apple Home app and Siri across your Apple devices."
- **Don't require an account or personal info**; optional cloud accounts come after HomeKit setup.
- Don't force other platforms' setup in the HomeKit flow.
- **Naming rules:** suggest good service names (never company names or model numbers); names use only letters, numbers, spaces and apostrophes, start and end with a letter or number, **no emoji** ("2nd garage door" OK, "#2 garage door" not). Discourage location words in names (assign the room instead of "kitchen light").

**Siri:** after setup show example phrases with the chosen names; later teach richer commands ("Hey Siri, set 'Movie Time'"); suggest zones and service groups; offer shortcuts **only** for functions HomeKit doesn't cover ("Order AC filters"); explain the difference between HomeKit voice control and shortcuts.

**Custom functionality:** explain what your app does vs. the Home app (build a scene with your accessory, then suggest adding other accessories in Home); reflect Home-app changes automatically and present conflicts visually; **ask before writing to the HomeKit database** — never overwrite silently. Cameras: don't cover the image with content; show a microphone button only for two-way audio.

**Icons and naming:** Apple-provided HomeKit icon only, for setup/instructional contexts, non-interactive (the Apple Home app icon may link to its App Store page); black/white/custom color like other tech icons; not in text. Keep HomeKit less prominent than your app. "HomeKit" (one word, capital H and K); "Apple Home" (first mention), then "the Home app". Use "works with HomeKit"/"compatible with Apple HomeKit" — never "HomeKit lightbulbs" or "HomeKit unlocked the door". Don't translate trademarks; say "iPhone or iPad", not "iOS devices"; no implied endorsement.

## iCloud
Source: https://developer.apple.com/design/human-interface-guidelines/icloud

- People turn on iCloud in Settings and expect apps to just work. If offering a choice, ask once at first launch: all data in iCloud or none.
- Don't ask which individual documents to keep in iCloud; automate file management.
- Keep content current, balancing storage/bandwidth; for very large documents, let people control downloads and indicate newer versions; show subtle progress for downloads over a few seconds.
- Respect paid storage: store only user-created, meaningful data — not regenerable app resources. Remember iCloud backups include each app's Documents folder.
- When iCloud is off or offline, **no alert** — at most an unobtrusive note that changes won't sync yet.
- Sync app state (last page read) and settings people want everywhere (not device-specific ones).
- **Warn before deleting** — deletion removes the document from iCloud and every device.
- Resolve version conflicts automatically when possible; otherwise an unobtrusive way to compare and choose, as early as possible.
- Include iCloud content in search.
- Games: save progress in iCloud (GameSave framework handles syncing, offline and conflict alerts).

## ID Verifier
Source: https://developer.apple.com/design/human-interface-guidelines/id-verifier

**iPhone only** (iOS 17+): reads ISO 18013-5 mobile IDs in person, no extra hardware.
- *Display Only* requests show data (name, age, portrait) in system UI without sending it to your app; *Data Transfer* requests (store/process address, birth date) require a legal need and an extra entitlement.
- Request the minimum — use an age threshold (`ageAtLeast`) rather than birth date or age.
- Register with Apple Business Register (if eligible) so your official name and logo appear.
- Start with a button labeled **"Verify Age"** or **"Verify Identity"**; no NFC/QR symbols; **never the Apple logo**.
- For Display Only, offer feedback buttons like "Matches Person" / "Doesn't Match Person".

## iMessage apps and stickers
Source: https://developer.apple.com/design/human-interface-guidelines/imessage-apps-and-stickers

Available in Messages conversations and in Messages/FaceTime effects; standalone or as an extension of your iOS/iPadOS app.
- One primary experience per iMessage app (separate apps for different functions/collections).
- Surface shareable app content (shopping lists, itineraries) or simple collaborative choices (where to eat).
- Put the most used features in the **compact** view (below the transcript); more in the **expanded** view.
- Text editing generally only in the expanded view (compact is keyboard-sized).
- Stickers: expressive, inclusive, versatile; legible on any background and when rotated/scaled; transparency helps. Give each a localized accessibility description.

**Icon sizes** (square corners — system masks)
| Usage | @2x px | @3x px |
|---|---|---|
| Messages, notifications | 148×110, 143×100, 120×90, 64×48, 54×40 | 180×135 (for 120×90), 96×72 (for 64×48), 81×60 (for 54×40) |
| Settings | 58×58 | 87×87 |
| App Store | 1024×1024 | 1024×1024 |

**Sticker sizes (@3x):** small **300×300**, regular **408×408**, large **618×618** px — pick one size per pack, never mix. Max **500 KB** per sticker. Formats: PNG (8-bit transparency, no animation), APNG (8-bit transparency, animated), GIF (single-color transparency, animated), JPEG (no transparency, no animation).

## Live Photos
Source: https://developer.apple.com/design/human-interface-guidelines/live-photos

- Apply edits/effects to all frames — or offer converting to a still.
- Never split a Live Photo into separate frames or audio.
- Sharing: preview the full Live Photo before sharing; always allow sharing as a still.
- Show download progress and when it's playable.
- Where unsupported, show a still — don't imitate playback.
- Distinguish Live Photos with a hint of motion (custom effect); otherwise use the system badge (with or without text) — **never a play button** that looks like video. Same badge corner every time.

## Mac Catalyst
Source: https://developer.apple.com/design/human-interface-guidelines/mac-catalyst

**iPadOS → macOS.** Good candidates already support drag and drop, keyboard navigation/shortcuts, multitasking resizing and multiple scenes. Poor candidates depend on gyroscope/accelerometer, rear camera, HealthKit, ARKit, handwriting or navigation.
- Automatic Mac features: pointer and keyboard focus, window management, toolbars, rich text editing and context menus, file management, menu bar, Settings integration; system UI takes a Mac look.
- **Idioms:** *iPad idiom* scales UI to **77%** (17 pt text → 13 pt); *Mac idiom* renders at 100% with more detail and performance but needs layout/text/image audit (separate asset catalog helps). Use text styles, avoid fixed font/view/layout sizes; keep customizations to those both platforms support.
- **Navigation:** replace an iPad tab bar with a sidebar split view (preferred) or segmented control; list top-level sections in the View menu; add Next/Previous buttons besides swipes.
- **Input mapping:** tap → click, touch and hold → click and hold, pan → click and drag; pinch/rotate map to trackpad gestures.
- Make a macOS-style app icon.
- **Layout:** split single columns into multiple; use regular size classes and reflow side by side on resize; inspectors beside content instead of popovers; move controls to the window toolbar (and menu bar); top-down flow; relocate edge/bottom buttons.
- **Menus:** every command in the menu bar (`UIMenuBuilder`, `UICommand`, `UIKeyCommand`); pop-up/pull-down menus convert automatically; add context menus to more objects.

## Machine learning
Source: https://developer.apple.com/design/human-interface-guidelines/machine-learning

Define the role ML plays, then design inputs and outputs around it.

**Role dimensions**
- *Critical vs. complementary* (Face ID vs. QuickType) — the more central, the more accuracy matters.
- *Private vs. public data* — sensitive data (health) demands higher reliability; always protect privacy.
- *Proactive vs. reactive* — unrequested suggestions get less tolerance for errors.
- *Visible vs. invisible* — invisible features struggle to show reliability or get feedback.
- *Dynamic vs. static* improvement — affects calibration and feedback design.

**Explicit feedback** (requested): only when necessary; always voluntary; describe consequences plainly ("Suggest less pop music", "Mute politics for a week" — not "Dislike"); icons only alongside text; offer several progressively specific options; act immediately and persist; use it to tune when/where results appear. (Favorites and social reactions are *implicit* feedback.)

**Implicit feedback:** secure it; tell people how info is gathered/shared and let them restrict it; don't trap people in their current tastes — preserve exploration; combine signals before inferring intent; withhold suggestions based on private/sensitive topics (shared devices); prioritize recent behavior; update at a cadence matching the mental model (typing: instantly; music: not continuously); expect UI changes to shift signals; beware confirmation bias.

**Calibration:** only if the feature can't work without it; secure; explain the benefit (what, not how); collect the minimum; once, early (except per-object calibration); quick and easy (no info people must look up, no hard actions); explicit goal with progress (Face ID ticks); help immediately when stalled without blaming; confirm success; cancellable anytime without judgment; editable/removable later.

**Mistakes:** anticipate, help people handle them, learn when it helps. Match corrective tools to severity (bad keyboard suggestion vs. missed flight). Easy fixes for frequent mistakes; keep updating with changing tastes and domain trends; avoid UI-heavy fixes that magnify errors; be extra careful with proactive features; watch for regressions elsewhere when optimizing one area.

**Corrections:** familiar tools (show the controls the automation used, like Photos auto-crop); apply instantly and persist; allow correcting corrections; if correcting is harder than doing it manually the feature fails; never rely on corrections to excuse poor quality; learn from them selectively; prefer guided (suggested alternatives) over freeform where possible.

**Multiple options:** prefer diverse options (routes: no tolls, scenic, highway); not too many — ideally one screen; most likely first (optionally preselected); easy to distinguish with brief descriptions highlighting differences; group large sets; learn from selections.

**Confidence:** verify confidence correlates with quality before using it; translate into human terms ("Because you listen to pop music", not "97% match"); use ranking or semantic categories ("high chance"); show numbers only where people expect statistics (weather, sports, polls); prefer actionable advice ("This is a good time to buy"); adapt presentation by threshold (ask to confirm when lower); hide low-confidence results, especially proactive ones.

**Attribution:** explain the basis ("Because you've read mysteries") to aid choice, soften mistakes, build mental models and trust; neither too specific (creepy) nor too general; factual, not emotional ("you've read nonfiction", not "you love nonfiction"); no statistical jargon except for inherently statistical content.

**Limitations:** set expectations up front for rare but serious limitations; demonstrate best use (placeholder hints like "Photos, People, Places…", live guidance like Memoji's lighting tips, suggest alternatives instead of empty results); explain causes of poor results ("doesn't work well in the dark"); announce when limitations are fixed.

## Maps
Source: https://developer.apple.com/design/human-interface-guidelines/maps

- Make maps interactive (zoom, pan, rotate); don't obscure them with non-interactive elements.
- Emphasis style: *default* (saturated, matches Apple Maps) or *muted* (desaturated, lets rich custom content stand out).
- Offer search plus category filters; style selections distinctly (outline + color); cluster overlapping POIs.
- **Apple logo and legal link must stay visible** (temporary covering OK): about **7 pt** side padding and **10 pt** above/below; keep them fixed to the map; place them **10 pt above** the lowest resting position of a pull-up card. (Not shown on maps under 200×100 px.)
- **Annotations:** match your style (tint; icon string of **2–3 characters** or an image). Consider selectable Apple map features with custom info (`MKMapFeatureOptions`). Overlays *above roads* (default; context visible) or *above labels* (hides the map beneath). Ensure controls contrast with the map (thin stroke, light shadow, blend modes).
- **Place cards:** styles automatic, callout (full or compact), caption ("Open in Apple Maps"), sheet. Full callout shows as a popover on iPad and a **sheet on iPhone**. Pick a style that fits the map size (compact for small maps with many pins), keep it readable across sizes (minimum width), avoid duplicating info, keep the location visible (offset). Outside a map, a place card **must include a map**; signal tappability with place names/addresses, a details button or a pin icon.
- **Indoor maps:** progressive detail by zoom; color + icons for categories; floor picker with short floor numbers; dimmed surrounding context; routes to nearby transit and handoff to Apple Maps; limit scrolling away from the venue; match your app's style, don't copy Apple Maps (IMDF).

## NFC
Source: https://developer.apple.com/design/human-interface-guidelines/nfc

- Devices need only be near tags — say **"scan" / "hold near"**, never "tap/touch".
- No jargon ("NFC", "Core NFC", "tag"): "Scan the [object]." / "Hold your iPhone near the [object] to learn more about it."
- Scanning sheet text: one complete sentence, sentence case, ending punctuation, names the object, updated for later scans ("Now hold your iPhone near another [object].").
- Support **both** background tag reading and in-app scanning (background isn't available on all devices or when the scanning sheet, Wallet/Apple Pay, camera or Airplane Mode is active, or before first unlock).

## Photo editing
Source: https://developer.apple.com/design/human-interface-guidelines/photo-editing

Photos editing extensions (edits saved as new versions).
- Confirm Cancel when edits exist (warn they'll be lost); no confirmation if nothing changed.
- **No custom top toolbar** — the modal already has one.
- Let people preview results before returning to Photos.
- Use your app icon as the extension icon.

## ResearchKit
Source: https://developer.apple.com/design/human-interface-guidelines/researchkit

**Onboarding, always in this order:**
1. **Introduction** — subject, purpose, call to action; quick login for existing participants.
2. **Eligibility** — as early as possible; only necessary requirements; plain language; easy entry.
3. **Informed consent** — comply with App Review consent rules and IRB/ethics requirements; split into digestible sections (data gathering, use, benefits, risks, time, withdrawal) with plain overviews and "Learn More" details; full form viewable before agreeing; optional comprehension quiz; then signature and contact info (usually email a PDF copy).
4. **Permissions** — explain why location/Health/etc. are needed; only request data critical to the study; notification permission if needed.

**Surveys:** say how many questions and how long; one question per screen; show progress; keep short (several short beats one long); explanatory text slightly smaller than the question; say when done.
**Active tasks** (speaking, tapping, walking, memory): plain instructions, stated requirements (time/conditions), clear completion.
**Profile and dashboard** (always accessible): edit changing data, upcoming activities, leave the study, view consent and privacy policy; dashboard for encouraging progress (daily progress, weekly assessments, comparisons to aggregates).

## SharePlay
Source: https://developer.apple.com/design/human-interface-guidelines/shareplay

Shared real-time activities across devices, alongside FaceTime or Messages. Each participant needs their own access to paid content.
- For real-time togetherness; offer share/save afterward for async collaboration (Freeform link).
- Choose shared view (watching, browsing) or per-person views (games) to fit the activity.
- Work across Apple platforms and contexts.
- Clear start: a button with the SharePlay symbol; also the share sheet.
- Frictionless joining: straight to shared content; sign-in/download/subscribe in a view that dismisses when done; consider provisional access or Family Sharing; defer nonessential setup.
- Short, clear activity descriptions (title, summary, poster) that don't truncate.
- Keep people oriented when someone changes things (system syncs playback; show who did what, like Freeform initials).
- **Term:** "SharePlay" as noun ("Join SharePlay") or verb in a control ("SharePlay Movie"); no adjectives ("virtual", "spatial"); never "SharePlayed/SharePlays/SharePlaying".
- **iOS/iPadOS:** support Picture in Picture for shared video.

## ShazamKit
Source: https://developer.apple.com/design/human-interface-guidelines/shazamkit

- Uses: genre-matched graphics, synced captions/sign language for accessibility, syncing experiences with media.
- Microphone needs a permission request with a clear reason.
- **Stop recording as soon as you have the sample.**
- Let people opt in before saving recognized songs to their iCloud library.

## Sign in with Apple
Source: https://developer.apple.com/design/human-interface-guidelines/sign-in-with-apple

Fast, private sign-in with the existing Apple Account; optional private relay email; Face ID/Touch ID and built-in 2FA; usable on all platforms including non-Apple.

**Offering it**
- Ask to sign in only in exchange for value; briefly explain benefits.
- **Delay sign-in** as long as possible (let people explore first).
- If an account is required, explain why and set up the account first, then offer sign-in options including Sign in with Apple.
- Consider linking existing accounts (matching email, or a suggestion in account settings).
- Commerce: account creation **after** purchase (guest checkout; on the Apple Pay confirmation page, without re-asking name/email).
- Welcome people immediately after sign-in; don't ask for unneeded info.
- Show the current method ("Using Sign in with Apple") in settings/account.

**Data**
- Minimize requests; explain why; mark what's legally/contractually **required** (terms, region, birth date, real-identity laws) vs. **optional** (with its benefit).
- **Never ask for a password** (unless they've stopped using Sign in with Apple).
- **Don't ask for a personal email if they chose a private relay address** — show the relay address, point to Settings › Apple Account › Password & Security › Apps using Apple Account, or use order/phone numbers for support.
- Ask for optional data later, in context (phone for text updates); never gate features on it.
- Be transparent — use the shared name/email (e.g. in a welcome).

**Buttons**
- Prominent: **no smaller than other sign-in buttons**, visible without scrolling.
- Prefer the system button (`ASAuthorizationAppleIDButton`): approved look, localized titles, adjustable corner radius, VoiceOver label. Titles: Sign in with Apple, Sign up with Apple, Continue with Apple — pick one and use consistently.
- Styles: **white** (dark backgrounds), **white with outline** (light backgrounds lacking contrast; not on dark/saturated), **black** (light backgrounds; not on dark).
- Minimum **140×30 pt**, margin **1/10 of button height**; corner radius may match your buttons (square to capsule).
- **Custom buttons** (App Review checks them): must be instantly recognizable; only Apple's downloadable logo artwork (never a custom Apple logo; never the logo alone as a button); logo file height = button height, no cropping, no extra vertical padding.
  - Fixed: titles (the three above only); shape (logo + text = rectangle; logo-only = circle or rectangle); logo and title both black or both white.
  - Adjustable: title font/weight/size, all-caps, background (black or white, subtle texture/gradient OK), corner radius, bezel stroke, shadow.
  - Logo + text: SVG/PDF any height; PNG only at **44 pt** height (iOS default). Title font size ≈ **43% of button height** (height ≈ 233% of font size). Keep default capitalization unless all-caps UI. Vertically center the title; logo matches height. Logo may be inset to align with other providers. Right margin **≥8% of button width**. Min **140×30 pt**, margin 1/10 height.
  - Logo-only: 1:1; SVG/PDF any size, PNG only at **44×44 pt**; no added horizontal padding; mask for circle/rounded shapes, never crop; margin ≥1/10 height.

## Siri
Source: https://developer.apple.com/design/human-interface-guidelines/siri

Apps expose actions (intents) and content (entities) through **App Intents**; adopting **App schema domains** (email, music, photos…) lets Siri AI handle natural requests with deeper context. Also: annotate on-screen views with entities (so "add this photo…" works), donate entities to the Spotlight index, donate actions so Siri can anticipate them.

**Best practices**
- Find your most popular actions and their contexts (hands-free, device) to prioritize what to expose.
- Use familiar terms (track vs. song vs. podcast as people would say it).
- Index relevant personal content (recent, favorites, wishlists), not everything (except categories like mail/messages).
- **No ads, marketing or IAP pitches** in Siri content.
- Custom responses only when built-in ones don't suffice; otherwise App Shortcuts for out-of-schema features; optional properties or snippets can enrich responses (may not always display).

**Response dialogue**
- Clear and specific ("Which soup?", not "Which one?"); as short as possible, no filler or humor.
- Works both spoken and shown — voice must stand alone.
- Inclusive, no unnecessary pronouns ("Who should I send it to?").
- Ask open-ended questions when the list is too long ("What kind of shoes are you interested in?").
- Device-independent wording; omit your app name (the system attributes).
- No offensive language; respect parental controls; remember others may hear.
- Situation-specific errors ("Sorry, we're out of chicken noodle soup").

**Editorial:** call it "Siri" — never she/her/him; never impersonate Siri or imitate Apple responses; don't use reserved phrases ("Call 911", "Hey Siri"); in localized copy translate only "Hey" in "Hey Siri" (e.g. "Oye Siri", "Dis Siri", "Hej Siri"; full table on source page) — never translate "Siri".

## Tap to Pay on iPhone
Source: https://developer.apple.com/design/human-interface-guidelines/tap-to-pay-on-iphone

**iPhone only.** Merchants accept contactless payments without hardware (requires a supported PSP, entitlement, ProximityReader).

**Enabling:** have merchants accept terms before customer-facing flows (onboarding, in-app messaging); terms only for admin users (others see "administrator access required"; enterprise admins may accept via web/other app); prompt OS updates first if the PSP requires them.

**Education:** tutorial on supported payment types — via Learn More, after accepting terms, for new users, and always findable in help/settings. Use Apple-approved marketing assets or `ProximityReaderDiscovery`. Custom tutorials must show starting checkout per payment type, positioning the card/wallet, PIN entry (including accessibility mode), and end with a chance to accept terms.

**Checkout**
- Always show the Tap to Pay option, enabled or not (present terms if needed, then the screen once configured).
- Prepare at launch and on every return to foreground (`prepare(using:)`); let merchants select it during configuration and show progress (determinate if the API reports progress).
- With multiple methods, make it findable without scrolling; if it's the only method, open it automatically at checkout. Make switching to hardware readers easy, without visiting settings.
- **Button label:** "Tap to Pay on iPhone" (or "Tap to Pay" if space is tight); if it's your only method you may reuse Charge/Checkout. With icons, use `wave.3.right.circle(.fill)`. **Never the Apple logo.** Style may match your buttons. Use these labels only for payments.
- Finalize the amount (tips etc.) and any pre-payment options before opening the Tap to Pay screen.

**Results:** start processing immediately (`returnReadResultImmediately`); show an authorization progress indicator after the checkmark animation; show approved/declined clearly; offer digital receipts (QR, text). On failure offer alternatives (cash, hardware, payment link, retry another card). Handle SCA PIN requests and offline-PIN markets with your PSP. Explain merchant-fixable errors (e.g. update iOS) and offer help/support contact.

**Other reads:** card reads without an amount use generic labels ("Look Up", "Store Card", "Verify", "Refund") — not "Tap to Pay". Separate, clearly labeled loyalty-card flows without payment wording.

## VoiceOver
Source: https://developer.apple.com/design/human-interface-guidelines/voiceover

- Provide descriptive accessibility labels for all key elements (system defaults are generic) and every custom element; keep them current.
- Describe meaningful images (only what the image itself conveys).
- Make charts/infographics fully accessible, including their interactions.
- Hide purely decorative images (`accessibilityHidden`).
- Unique, concise screen titles and accurate section headings.
- Group, order and link elements whose relationships are only visual (e.g. image + caption) — `shouldGroupAccessibilityChildren`; VoiceOver follows reading order of the locale.
- Announce visible content/layout changes (`AccessibilityNotification`).
- Support the rotor (headings, links, custom entries) — `AccessibilityRotorEntry`.

## Wallet
Source: https://developer.apple.com/design/human-interface-guidelines/wallet

**Passes**
- Offer to add new passes with one tap after the action that creates them; for frequent predictable passes (flight check-in), add in the background after a one-time authorization.
- Suggest adding passes created elsewhere on next app open — once; don't ask again if declined.
- Add related passes as a group (multi-leg flights, ticket sets).
- Show an **Add to Apple Wallet** button (`PKAddPassButton`) where pass info appears for passes not in Wallet; "View in Wallet" links for ones that are.
- Set expiration, relevant date and voided properly so Wallet hides expired passes.
- **Get permission before deleting passes** (setting or alert).
- Provide relevance (time/place) so passes surface on the Lock Screen (gym card on arrival); event tickets can start Live Activities.
- Keep passes updated (gate changes); **change messages only for time-critical updates — never marketing**.

**Anatomy:** logo + logo text and header fields (visible when collapsed), primary, secondary/auxiliary, footer, back fields; semantic tags (required for poster event tickets and semantic boarding passes — include fields too for older iOS) enable surfacing and featured actions; additional info sheets; back for rarely needed info (legal).

**Design:** use Pass Designer; design a clean Wallet-native pass, not a replica of the physical card; works on all devices (Watch shows less; don't pad images; nothing essential in elements some devices hide); uncluttered front with essentials in the header; instantly identifiable branding; strong text/background contrast; device-neutral wording (not "Slide to view").
- Styles: boarding pass (one trip; semantic tags for airlines), coupon, event ticket (poster style with full-art background, or standard), store card (show balance), poster generic, generic (gym card, coat check).

**Images** (PNG @2x and @3x; small files; no embedded text or barcodes — use fields and Pass Designer barcodes)
| Image | Filename | Size (pt) | Styles |
|---|---|---|---|
| Logo | logo.png | 50 tall, 50–160 wide | Non-semantic passes (boarding, coupon, non-poster event, generic, store card) — no inner drop shadows |
| Primary logo | primaryLogo.png | 30 tall, 30–126 wide | Semantic airline, poster event, poster generic |
| Secondary logo | secondaryLogo.png | 12 tall, 12–135 wide | Poster event (bottom trailing) |
| Icon | icon.png | 38×38 (system rounds corners) | All |
| Strip | strip.png | 375×144 | Coupon, store card — keep text areas clear, no embedded text |
| Thumbnail | thumbnail.png | 90 tall, 60–90 wide (rounded corners, transparent PNG) | Event ticket, generic |
| Background | background.png | 343×503 | Event tickets (non-poster) |
| Poster artwork | artwork.png | 358×448 (bottom covered by material strip; mind barcode) | Poster event, poster generic |
| Footer | footer.png | 268×15 | Airline boarding passes |

**Order tracking** (iOS 17+)
- Add orders to Wallet automatically after Apple Pay (`PKPaymentOrderDetails`) or via the **Track with Apple Wallet** button on confirmation/status pages and emails.
- Provide order info immediately (even "Check back later for full order details"); update fulfillment and status promptly (Order Placed, Processing, Ready for Pickup, Picked Up, Out for Delivery, Delivered, Issue, Canceled).
- Logo **300×300 px** PNG/JPEG with opaque background; product images **300×300 px**, plain depictions on solid opaque backgrounds.
- Brief, clear, localized text; prices must match the confirmed final price.
- Provide a universal link to order management; describe every line item (name, price, image; optional PDF receipts); prioritized list of your apps; avoid duplicate notifications; multiple contact methods (website required; Messages for Business, phone, email, support optional).
- Fulfillments: ETA, direct carrier tracking link (plus number), pickup barcode, clear instructions; keep the screen focused on tracking; carrier name if known (else default "Track Shipment"); use detailed statuses only if you have carrier data, otherwise `shipped`; friendly, accurate status text; for Issue/Canceled explain why and what to do.

**Identity verification** (iPhone, iOS 16+; Verify with Wallet)
- Show the button only on supported devices; have a fallback method.
- Ask only at the moment you need it (not at account creation).
- Purpose string: brief, direct, complete sentence, sentence case, active voice, period ("Applicable state law requires [App] to verify your driving privileges.").
- Request the minimum (age threshold, not birth date) and state retention (period, indefinite, or only for this verification).
- Button labels: Verify Age, Verify Identity, Continue (part of a longer flow), Verify with Wallet (generic); multiline variants; always white on black (outline style for dark backgrounds); adjustable corner radius.
