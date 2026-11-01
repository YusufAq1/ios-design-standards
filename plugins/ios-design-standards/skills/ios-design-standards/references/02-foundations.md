# Foundations

Summarized from Apple's Human Interface Guidelines (iOS and iPadOS guidance only). Paraphrased; exact specs kept. Open the source link for Apple's exact wording.

## Accessibility
Source: https://developer.apple.com/design/human-interface-guidelines/accessibility

Goal: an interface that is intuitive (familiar, consistent), perceivable (never relies on one sense) and adaptable (honors system accessibility settings). Audit with Accessibility Inspector; declare support on the App Store via Accessibility Nutrition Labels.

**Vision**
- Let text scale to at least 200% — adopt Dynamic Type or offer equivalent custom sizing.
- Custom type defaults (iOS/iPadOS): **default 17 pt, minimum 11 pt**. Thin custom weights need larger sizes.
- Contrast (WCAG AA, used by Accessibility Inspector): **text up to 17 pt → 4.5:1; 18 pt+ → 3:1; bold text any size → 3:1**. If defaults fall short, at least provide higher-contrast colors when Increase Contrast is on. Check both light and dark appearances.
- Prefer system colors — they ship accessible variants that adapt automatically.
- Never use color alone to signal meaning or state (watch red-green, blue-orange); add shapes, icons or text. Consider user-customizable color schemes (charts, game characters).
- Label everything for VoiceOver.

**Hearing**
- Don't deliver dialogue or crucial info through audio only. Offer captions, subtitles, audio descriptions and/or transcripts as appropriate, with customizable presentation.
- Pair audio cues with haptics. iOS/iPadOS also offers Music Haptics and Audio Graphs.
- Pair audio cues with visual cues, especially for off-screen events.

**Mobility**
- Control size (iOS/iPadOS): **default 44×44 pt, minimum 28×28 pt**.
- Spacing: about **12 pt padding around bezeled elements; about 24 pt around the visible edges of unbezeled elements**.
- Use the simplest gesture for frequent actions; avoid custom multi-finger/multi-hand gestures.
- Every gesture-driven action needs an onscreen alternative (e.g. swipe-to-dismiss also gets a button).
- Label elements so Voice Control works; integrate with Siri and Shortcuts for voice-only task flows.
- Test with VoiceOver, AssistiveTouch, Full Keyboard Access, Pointer Control and Switch Control.

**Speech**
- App must be fully usable with Full Keyboard Access; don't override system keyboard shortcuts.
- Support Switch Control navigation.

**Cognitive**
- Keep interactions simple and consistent; prefer system gestures over custom ones.
- Avoid UI that auto-dismisses on a timer; prefer explicit dismissal.
- Games: consider adjustable difficulty, reaction time, control assistance.
- Don't autoplay audio/video without discoverable start/stop controls; consider a global opt-out.
- Honor Dim Flashing Lights in video playback.
- Honor Reduce Motion: tighten springs (less bounce), tie animation directly to gestures, avoid animating z-depth, replace x/y/z transitions with fades, avoid animating into/out of blurs.
- Assistive Access (iOS/iPadOS): strip to core features, one interaction per screen, double-confirm hard-to-undo actions (e.g. delete).

## App icons
Source: https://developer.apple.com/design/human-interface-guidelines/app-icons

**Spec (iOS/iPadOS):** square layout **1024×1024 px**, system masks to a rounded rectangle; layered. Appearances: default, dark, clear light, clear dark, tinted light, tinted dark. Color spaces: sRGB, Gray Gamma 2.2, Display P3. System scales down for Settings, notifications, etc.

**Layers and format**
- Build a background layer + one or more foreground layers; the system adds Liquid Glass effects (specular highlights, refraction, translucency).
- Preferred: layered Icon Composer file (ships with Xcode). A flat PNG is allowed, but the system then auto-segments it and only applies glass to large simple shapes — not text or thin lines.
- Foreground layers: crisp edges (no feathering); vary opacity for depth.
- Background: solid color or gradient (made in Icon Composer); any imported background must be full-bleed and opaque.
- Import vectors (SVG/PDF), outline text; use PNG for raster/mesh gradients.
- Provide square, **unmasked** layers — pre-rounded corners break highlights and look jagged. Keep key content centered (use Apple's production template grids).

**Design**
- One simple core idea, few shapes, simple background; no need to fill the canvas.
- Consistent icon across every platform you ship on.
- Filled, overlapping shapes with transparency read well.
- Avoid text unless essential to the brand; no "Play"/"Watch"/"New"-style words.
- Prefer illustration to photos; no screenshots or copies of standard UI; avoid hairlines and sharp corners.
- Never depict Apple hardware.
- Don't bake in shadows, bevels, glows, blur or highlights — the system adds dynamic ones. Group layers in Icon Composer to apply effects together.

**Appearances**
- Keep the same core features across default/dark/clear/tinted; don't swap elements between variants.
- Dark/tinted versions should sit comfortably next to system icons; derive dark from the light icon, avoid overly bright imagery; colored backgrounds give dark icons the most contrast.
- Alternate icons (user-selectable in settings) are allowed; each needs its own dark, clear and tinted variants, must clearly relate to your app, and goes through App Review.

## Branding
Source: https://developer.apple.com/design/human-interface-guidelines/branding

- Express brand through voice and tone in copy.
- Use the accent color sparingly — primary actions, status (badges, selected tab). Brand color can live in the content layer under Liquid Glass controls.
- Custom fonts: fine for headlines; must stay legible and support Bold Text and Dynamic Type. System font for body/captions works best.
- Brand standard components rather than inventing new ones; keep size, placement and behavior platform-familiar.
- Content first: don't spend screen space on logo-only elements; don't repeat the logo throughout the app.
- Keep standard patterns (placement, symbols, navigation, modality) even in a stylized UI.
- Launch screen is not a branding moment; put branding in a welcome/onboarding screen if needed.
- No Apple trademarks in the app name or images.

## Color
Source: https://developer.apple.com/design/human-interface-guidelines/color

**Best practices**
- One color = one meaning. Don't reuse the "interactive" color for plain text.
- Every color must work in light, dark and Increase Contrast. Prefer system colors (they already have all variants). Custom colors need light + dark variants, each with a clearly stronger high-contrast version. Provide light and dark even if you ship one appearance — Liquid Glass adapts to both.
- Test under bright sun and dim light; test on real devices (True Tone shifts white point; reading/photo/video/game apps can set a white-point adaptivity style).
- Artwork and translucent bars change how nearby colors read; adjust surrounding colors when content changes (e.g. Maps goes dark in satellite mode).
- If users pick colors, use the system color picker.

**Inclusive color**
- Never rely on color alone for identity, interactivity or essential info — add labels or glyph shapes.
- Ensure contrast; avoid color pairs color-blind people can't separate.
- Color meanings vary by culture (red = danger vs. luck).

**System colors**
- Don't hard-code system color values — they change between releases. Use the APIs (`Color`, `UIColor`).
- Use dynamic semantic colors for their stated purpose only (don't use `separator` as text color or `secondaryLabel` as a background).
- System palette: red, orange, yellow, green, mint, teal, cyan, blue, indigo, purple, pink, brown; grays `systemGray`–`systemGray6` (SwiftUI `gray`). Each has light, dark and increased-contrast values (see source page).

**Liquid Glass color**
- Glass is colorless by default and picks up what's behind it. Tinting glass is for emphasis (e.g. prominent buttons).
- Small elements (toolbars, tab bars) flip between light and dark glass; their symbols/text go monochrome automatically. Large elements (sidebars) are more opaque.
- Use color on glass sparingly — status or the primary action. To emphasize a primary action, tint the **background**, not the symbol/text (as the system does for Done). Don't tint the backgrounds of multiple controls.
- Colorful app backgrounds → keep toolbars/tab bars monochrome or choose a clearly different accent. Monochrome apps → brand color as accent works well.
- Keep resting states legible: avoid similar colors between content and the controls floating above it (e.g. the top of a scroll view).

**Color management**
- Embed color profiles in images; sRGB is accurate on most displays.
- Wide color: Display P3, 16 bits per channel, export PNG (design it on a wide-color display).
- Provide sRGB/P3-specific variants in the asset catalog when similar P3 colors or P3 gradients clip on sRGB.

**iOS/iPadOS specifics**
- Two background sets, each with primary / secondary / tertiary levels: `systemBackground…` (plain) and `systemGroupedBackground…` (grouped table views). Primary = whole view; secondary = groups within it; tertiary = groups within those.
- Foreground semantic colors: `label`, `secondaryLabel`, `tertiaryLabel`, `quaternaryLabel`, `placeholderText`, `separator` (lets content show through), `opaqueSeparator`, `link`.

## Dark Mode
Source: https://developer.apple.com/design/human-interface-guidelines/dark-mode

- People expect every app to follow their system appearance. **Don't add an app-specific light/dark setting.**
- Look good in light, dark and Auto (which can switch while the app is running).
- Test legibility in Dark Mode with Increase Contrast and Reduce Transparency, separately and together.
- A permanently dark UI is acceptable only rarely — e.g. immersive media viewing.
- Dark palette = dimmer backgrounds, brighter foregrounds; not a straight inversion.
- Use adaptive semantic colors. Custom colors → Color Set in the asset catalog with light and dark variants; no hard-coded values.
- Contrast: **never below 4.5:1; aim for 7:1** for custom foreground/background pairs, especially small text.
- Slightly darken content images with white backgrounds so they don't glow.
- Use SF Symbols (adapt automatically). Make separate light/dark versions of custom icons if needed (e.g. add an outline in one mode). Full-color images: one asset if it works in both modes, otherwise light + dark variants in one named image set.
- Use system label colors and system text fields/views.
- **iOS/iPadOS:** two background sets in Dark Mode — *base* (dimmer, recedes) and *elevated* (brighter, comes forward for popovers, sheets, multitasking and multiple windows). Prefer system backgrounds so this elevation works; custom backgrounds break it.

## Icons (interface icons / glyphs)
Source: https://developer.apple.com/design/human-interface-guidelines/icons

- Simple, recognizable, familiar metaphor tied directly to the action or content.
- Consistent size, detail, stroke weight and perspective across all icons, custom and system. Adjust dimensions for visual weight.
- Match icon weight to adjacent text unless you want emphasis.
- Optically center asymmetric icons — bake small padding into the asset.
- No selected-state variant needed for system components (toolbars, tab bars, buttons) — the system handles it.
- Inclusive imagery: gender-neutral figures, culturally recognizable.
- Text in icons only when essential (e.g. formatting); localize characters; abstract text blocks need an RTL-flipped version.
- Custom icons in vector (PDF/SVG) — or make a custom SF Symbol. PNG would need every resolution.
- Give every custom icon an accessibility label.
- Don't draw Apple hardware; use Apple Design Resources or the product SF Symbols if you must.

**Standard SF Symbols for common actions**
| Action | Symbol |
|---|---|
| Cut / Copy / Paste | `scissors` / `document.on.document` / `document.on.clipboard` |
| Done / Cancel or Close | `checkmark` / `xmark` |
| Delete | `trash` |
| Undo / Redo | `arrow.uturn.backward` / `arrow.uturn.forward` |
| Compose / Duplicate / Rename | `square.and.pencil` / `plus.square.on.square` / `pencil` |
| Move to (folder) / Attach | `folder` / `paperclip` |
| Add / More | `plus` / `ellipsis` |
| Select / Deselect | `checkmark.circle` / `xmark` |
| Bold / Italic / Underline | `bold` / `italic` / `underline` |
| Superscript / Subscript | `textformat.superscript` / `textformat.subscript` |
| Align left / center / justify / right | `text.alignleft` / `text.aligncenter` / `text.justify` / `text.alignright` |
| Search / Find (and replace, next, previous) | `magnifyingglass` / `text.page.badge.magnifyingglass` |
| Filter | `line.3.horizontal.decrease` |
| Share or Export / Print | `square.and.arrow.up` / `printer` |
| Account, User, Profile | `person.crop.circle` |
| Like / Dislike | `hand.thumbsup` / `hand.thumbsdown` |
| Bring to front / Send to back | `square.3.layers.3d.top.filled` / `square.3.layers.3d.bottom.filled` |
| Bring forward / Send backward | `square.2.layers.3d.top.filled` / `square.2.layers.3d.bottom.filled` |
| Alarm / Archive / Calendar | `alarm` / `archivebox` / `calendar` |

## Images
Source: https://developer.apple.com/design/human-interface-guidelines/images

- Points are resolution-independent; scale factor sets pixels per point.
- **Scale factors: iOS @2x and @3x; iPadOS @2x.** Supply every bitmap at each, named with the @2x/@3x suffix in the asset catalog.
- Design at 1x and scale up; put vector control points on whole values so they stay pixel-aligned.

| Image type | Format |
|---|---|
| Bitmap/raster | De-interlaced PNG |
| PNG not needing 24-bit color | 8-bit palette |
| Photos | JPEG (optimized) or HEIC |
| Stereo/spatial photos | Stereo HEIC |
| Flat icons/artwork needing scaling | PDF or SVG |

- Embed a color profile in every image; test on several real devices for pixelation/stretching.

## Immersive experiences
Source: https://developer.apple.com/design/human-interface-guidelines/immersive-experiences

**Not supported on iOS or iPadOS** — visionOS only (Shared Space vs. Full Space; mixed, progressive and full immersion). Only relevant if the iOS app also ships on Apple Vision Pro.

## Inclusion
Source: https://developer.apple.com/design/human-interface-guidelines/inclusion

- Inclusion is more than "not offensive": design from many perspectives (age, gender, race, sexuality, physical/cognitive attributes, permanent/temporary/situational disability, language, culture, religion, education, politics, economic context).
- **Language:** clear, direct, respectful tone (an academic tone can exclude). Address people as "you/your", not "the user/the player"; reserve "we/our" for your company. Define jargon or avoid it. Replace idioms and colloquialisms with plain language (some have exclusionary origins). Use humor cautiously — it rarely translates.
- **Approachable:** simple platform-familiar UI; skippable onboarding.
- **Gender:** avoid unnecessary gendered references ("subscribers can post recipes" not "his or her recipes"). Let people customize avatars/characters. Use nongendered figures for generic people (SF Symbols `person`, `figure`). Ask for gender only when needed (health/legal) and offer inclusive options (nonbinary, self-identify, decline to state) plus pronouns.
- **People and settings:** show diverse people, bodies, ages and abilities; avoid occupational and hero/villain stereotypes; avoid unnecessary displays of affluence.
- **Stereotypes:** don't assume family structures or shared life experiences. Security questions should be universal ("name of your first friend"), not context-specific ("make of your first car").
- **Disability:** support VoiceOver, Display Accommodations, captions, Switch Control, Speak Screen. Disability is a spectrum and can be temporary or situational. Include disabled people in imagery; don't use disability as a metaphor for something negative; write people-first and follow how communities self-identify.
- **Languages:** internationalize first, then localize. Plain language, gender-neutral copy and SF Symbols ease localization. Check color meanings per locale (white = mourning in some places, purity in others).

## Layout
Source: https://developer.apple.com/design/human-interface-guidelines/layout

**Visual hierarchy**
- Most important content at the top and leading edge (reading order). Use system components so RTL flips automatically.
- Align to aid scanning; indent to show subordination.
- Group related items with negative space, containers or separators.
- Progressive disclosure (disclosure triangles, menus, nested views, scrollable sections) to cut clutter.
- Separate controls from content with Liquid Glass. **Don't put solid or semi-opaque backgrounds under controls — use a scroll edge effect.** Full-screen background content should extend under sidebars, toolbars and tab bars. If a sidebar/inspector would cover key image content, use a background extension effect (`backgroundExtensionEffect()`, `UIBackgroundExtensionView`).

**Adaptability** — handle all of:
- Compact/regular size classes, every screen size, orientation and aspect ratio
- Dynamic Island, external displays, Display Zoom, resizable iPad windows, iPhone Mirroring on Mac
- Text-size changes, RTL/LTR, locale formatting, text length

Rules:
- Use SwiftUI or Auto Layout; respect safe areas, margins and layout guides.
- Even orientation-locked apps must resize well.
- Dynamic Type: let side-by-side views stack vertically, rows grow taller, single-line rows wrap to multiple lines — never crop or overlap text.
- Test extremes first (largest and smallest layouts, longest localizations, largest text) in Device Hub simulators.
- Scale background art to fill; never distort aspect ratio; expect very wide or very tall windows.

**Size classes (iOS/iPadOS)**
- Horizontal and vertical are each compact or regular; any combination can occur (full screen, Slide Over, split view, iPhone Mirroring).
- **Base layout on size class, never on device type or orientation.**
- Design for all combinations — don't waste iPad height or width.
- Same functionality at every size; you may show more of it in larger spaces (e.g. tab bar → sidebar, overflow items surfaced).
- The idiom (device type) doesn't change on resize; keep the layout familiar for that platform.

**Guides and safe areas**
- Use system layout guides for standard margins and readable text width.
- Always keep content and controls inside the safe area so the status bar, Dynamic Island, home indicator, toolbars and tab bars don't obscure them.

## Materials
Source: https://developer.apple.com/design/human-interface-guidelines/materials

Two kinds: **Liquid Glass** (the floating functional layer for controls and navigation) and **standard materials** (blur/vibrancy within the content layer).

**Liquid Glass**
- Only for controls/navigation (tab bars, toolbars, sidebars). **Never in the content layer** — use standard materials there. Exception: transient interactive controls like sliders and toggles take on glass while being touched.
- System components adopt it automatically. Apply it to custom controls sparingly — only the most important ones.
- Variants: **regular** (blurs and adjusts luminosity; default for most components and anything text-heavy — alerts, sidebars, popovers) and **clear** (highly translucent; only over rich media like photos and video).
- Clear glass over bright content: add a **dark dimming layer at 35% opacity**. Not needed over dark content or with AVKit playback controls (they dim themselves).
- Appearance changes with the user's Liquid Glass preference, Reduce Transparency and Increase Contrast — test them.

**Standard materials**
- Choose by semantic purpose, not by the color it appears to give.
- Put system vibrant colors on top of materials for guaranteed legibility.
- Thicker = more opaque = better for fine text; thinner = more context visible.
- **iOS/iPadOS materials:** ultra-thin, thin, regular (default), thick.
- Vibrancy for labels: `label`, `secondaryLabel`, `tertiaryLabel`, `quaternaryLabel` — **don't use quaternary on thin or ultra-thin** (too little contrast). Fills: `fill`, `secondaryFill`, `tertiaryFill`. Separator: one `separator` style for all materials.

## Motion
Source: https://developer.apple.com/design/human-interface-guidelines/motion

- System components already animate (Liquid Glass reacts more strongly to touch than to trackpad). Custom motion must earn its place.
- No motion for its own sake — excess animation distracts and can cause discomfort.
- Motion must be optional: never the only carrier of important information; back it up with haptics or audio. Honor Reduce Motion (see Accessibility).
- Feedback motion should be realistic and follow the gesture (a view pulled down from the top is dismissed upward, not sideways).
- Keep feedback animation brief and precise.
- Don't animate frequent interactions on custom elements.
- Animations must be interruptible — never make people wait, especially for repeated ones.
- Use SF Symbol animations where they fit.
- Games: hold a steady 30–60 fps with good defaults per device; offer performance/battery options (e.g. power modes when plugged in).

## Privacy
Source: https://developer.apple.com/design/human-interface-guidelines/privacy

You must declare privacy practices and collected data in App Store Connect for the product page ("privacy nutrition labels").

**Best practices**
- Request only data a feature actually needs, and only once the person shows interest in that feature. Keep requests narrow.
- Be transparent about collection and use. Respect Hide My Email and Mail Privacy Protection; understand App Tracking Transparency obligations.
- Process on device where possible (Neural Engine, Create ML). Use system protections (e.g. CloudKit encryption).

**What needs permission:** personal data (location, health, financial, contacts, identifiers); user content (mail, messages, calendar, contacts, gameplay, Apple Music, HomeKit, photos/audio/video); protected resources (Bluetooth, home automation, Wi-Fi, local network); camera and microphone; the advertising identifier (tracking).

**Requesting permission**
- Ask in context, at the moment of use. Ask at launch only if the app can't function without it (e.g. navigation needs location).
- Purpose string: one brief, specific, complete sentence; sentence case; active voice; ends with a period. Good: "The app records during the night to detect snoring sounds." Bad: vague passive ("…needed for a better experience") or bare commands ("Turn on microphone access.").
- **Pre-permission screens** (optional, before camera/mic/location/contacts/calendar/tracking alerts): exactly **one** button, titled "Continue" or "Next" (never "Allow"), that opens the system alert. No close/cancel/skip or other actions, unless required for legal consent.
- **Tracking (ATT):** show the system alert before collecting any tracking data. Pre-alert screens must not mislead. **Rejected by App Review:** offering incentives, screens that imitate a permission request, showing a picture of the alert, or annotating/pointing at the alert. A legally required consent screen before or after ATT is allowed (Guideline 5.1.1(iv)).

**Location button (iOS/iPadOS)**
- Core Location's button grants one-time location access at the moment of need (attach location to a post, find a store, identify a plant). Good when people usually pick "Allow Once".
- Customizable: system title (e.g. "Current Location", "Share My Current Location"), filled or outlined glyph, background/title/glyph colors, corner radius. Nothing else.
- Must stay legible (system warns on low contrast/translucency); text must fit without truncation at all accessibility sizes and in every language. If the system detects persistent problems, the button stops granting location.

**Protecting data**
- Don't rely on passwords alone: prefer passkeys; otherwise require 2FA. Gate signed-in apps with Face ID/Touch ID.
- Store secrets in the Keychain — never in plain-text files.
- Don't invent authentication schemes; use passkeys, Sign in with Apple, Password AutoFill.

## Right to left (RTL)
Source: https://developer.apple.com/design/human-interface-guidelines/right-to-left

System components flip automatically for Arabic, Hebrew, etc. Fine-tune with these rules:

**Text**
- Mirror text alignment with the interface. One- and two-line text follows the interface direction; paragraphs (3+ lines) align to their own language. All items in a list share one alignment, even if mixed scripts.

**Numbers**
- Hebrew uses Western Arabic numerals; Arabic may use Western or Eastern — check per locale for number-heavy apps.
- Never reverse the digits within a number (phone numbers, card numbers, "541").
- Do reverse the *order* of numerals that show progress or sequence (slider scales, ratings).

**Controls**
- Flip progress controls (sliders, progress bars) and their end glyphs.
- Flip navigation/ordered-sequence controls (back button points right; next/previous).
- Don't flip controls meaning a real direction or pointing at a screen area.
- Next to all-caps Latin text, raise Arabic/Hebrew font size about **2 pt** to balance.

**Images**
- Don't flip photos, illustrations or artwork (changes meaning; may violate copyright); make a new version if direction matters.
- Reverse the positions of images whose order is meaningful.

**Interface icons**
- SF Symbols include RTL and localized variants; set directionality on custom symbols.
- Flip icons that depict text/reading direction or forward/backward motion (e.g. speaker sound waves).
- Localize icons containing actual text; replace text-based icons unrelated to writing with non-text designs.
- Never flip logos, universal marks (checkmark) or real-world objects (clocks, right-handed tools).
- For complex icons, decide per component (badges, slashes, magnifiers) for meaning and balance.

## SF Symbols
Source: https://developer.apple.com/design/human-interface-guidelines/sf-symbols

Thousands of symbols that align with the San Francisco font at every weight/size. Availability depends on OS version. **License forbids using symbols (or look-alikes) in app icons, logos or trademarks.**

**Rendering modes** (symbols are built from primary/secondary/tertiary layers)
- Monochrome — one color.
- Hierarchical — one color at varying opacity per layer (depth).
- Palette — one color per layer (two colors on a 3-layer symbol → secondary and tertiary share).
- Multicolor — intrinsic meaningful colors (green `leaf`, red `trash.slash`).
- Use system colors so symbols adapt to Dark Mode, vibrancy and accessibility. Check legibility per context; "automatic" picks the preferred mode.
- Gradients (SF Symbols 7+): linear gradient from one color; best at large sizes.
- Variable color: shows a changing value (capacity, signal, volume) by lighting layers at thresholds 0–100%. Use for change, not depth (use Hierarchical for depth).

**Weights and scales**
- 9 weights (ultralight → black) matching San Francisco weights — match adjacent text.
- 3 scales: small, medium (default), large, relative to cap height — change emphasis without breaking weight match.

**Variants**
- Outline (default; next to text, toolbars, lists), fill (emphasis/selection; iOS tab bars and swipe actions), slash (unavailable), enclosed in circle/square (better legibility at small sizes). Many containers pick the variant automatically (tab bar → fill, toolbar → outline).
- Script-specific variants (Latin, Arabic, Hebrew, Hindi, Thai, CJK, Cyrillic, Devanagari, Indic numerals) switch with device language.

**Animations**
- Appear, Disappear; Bounce (one-off "something happened"); Scale (persists — selection emphasis); Pulse (opacity, ongoing activity); Variable color (cumulative or iterative; progress/connecting; open vs. closed loop); Replace (down-up = state change, up-up = forward progress, off-up = emphasize next state); Magic Replace (default; smart morph between related symbols, e.g. slash on/off); Wiggle (call attention); Breathe (opacity + size, ongoing activity like recording); Rotate (whole or by layer); Draw On/Off (SF Symbols 7+, progress or reinforcing direction).
- Use judiciously; each animation must have a clear purpose that matches what it conveys and fits your app's tone.

**Custom symbols**
- Start from an exported template of a similar symbol; match system detail, optical weight, alignment, position and perspective. Simple, recognizable, inclusive, directly related.
- Apple product/feature symbols can be displayed but **not customized** (marked with an Info badge).
- Annotate layers for rendering modes and animation; set Z-order for variable color; draw whole shapes and use erase layers rather than cutouts so animations work. Test with every animation preset.
- Use negative side margins (named like `left-margin-Regular-M`) for optical alignment of badged symbols.
- Build badges/enclosures with the SF Symbols component library, not baked in.
- Give every custom symbol an accessibility label. No replicas of Apple products.

## Spatial layout
Source: https://developer.apple.com/design/human-interface-guidelines/spatial-layout

**Not supported on iOS or iPadOS** — visionOS only (field of view, depth, dynamic vs. fixed scale, 60 pt control spacing for eye targeting). Only relevant if the app also runs on Apple Vision Pro.

## Typography
Source: https://developer.apple.com/design/human-interface-guidelines/typography

**Legibility**
- iOS/iPadOS: **default 17 pt, minimum 11 pt** (custom and system fonts). Thin weights need bigger sizes.
- Avoid Ultralight, Thin and Light; prefer Regular, Medium, Semibold, Bold.
- Test legibility in context; fix with larger size, more contrast or a system font.

**Hierarchy**
- Use weight, size and color for hierarchy, and keep it intact when text size changes.
- Use as few typefaces as possible.
- When text grows, prioritize content people care about (body, dialog) over chrome (tab titles, transient values).

**System fonts**
- iOS/iPadOS system font is **SF Pro**; **New York** (serif) is also available. SF family also includes SF Compact, SF Mono, SF Arabic/Armenian/Georgian/Hebrew, and Rounded variants.
- Variable fonts with dynamic optical sizing — no need to pick Text vs. Display. Weights Ultralight–Black; SF widths include Condensed and Expanded. SF Symbols weights match.
- **Don't embed system fonts** — access them via `Font.Design` (`.default`, `.serif`, `.rounded`, `.monospaced`).
- Prefer built-in text styles (they give Dynamic Type for free). Modify with symbolic traits (bold → emphasized weight; loose leading for long/wide text, tight leading for constrained rows — but never tight for 3+ lines).
- Mockups: the system adjusts tracking per size automatically; apply the tracking table manually in design tools.

**Custom fonts**
- Must be legible at the recommended sizes and must support Dynamic Type and Bold Text like system fonts do. Unity games: use Apple's Unity plug-ins or offer their own text-size control.

**Dynamic Type**
- Layout must work at every size including the Larger Accessibility Sizes (Settings › Accessibility › Display & Text Size › Larger Text).
- Scale meaningful icons with text (SF Symbols do this automatically).
- Minimize truncation: show as much at the largest accessibility size as at the largest standard size; let labels use multiple lines; don't truncate in scroll views unless there's a way to read the full text.
- At large sizes, stack secondary items (glyphs, timestamps) below text and reduce column count (`isAccessibilityCategory`).
- Keep primary elements near the top at every size.

**iOS/iPadOS Dynamic Type sizes — size/leading in points**

Weights: Headline is Semibold; all other styles Regular. Emphasized (bold trait): Large Title, Title 1, Title 2 → Bold; all others → Semibold.

| Style | xS | S | M | **L (default)** | xL | xxL | xxxL | AX1 | AX2 | AX3 | AX4 | AX5 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Large Title | 31/38 | 32/39 | 33/40 | **34/41** | 36/43 | 38/46 | 40/48 | 44/52 | 48/57 | 52/61 | 56/66 | 60/70 |
| Title 1 | 25/31 | 26/32 | 27/33 | **28/34** | 30/37 | 32/39 | 34/41 | 38/46 | 43/51 | 48/57 | 53/62 | 58/68 |
| Title 2 | 19/24 | 20/25 | 21/26 | **22/28** | 24/30 | 26/32 | 28/34 | 34/41 | 39/47 | 44/52 | 50/59 | 56/66 |
| Title 3 | 17/22 | 18/23 | 19/24 | **20/25** | 22/28 | 24/30 | 26/32 | 31/38 | 37/44 | 43/51 | 49/58 | 55/65 |
| Headline | 14/19 | 15/20 | 16/21 | **17/22** | 19/24 | 21/26 | 23/29 | 28/34 | 33/40 | 40/48 | 47/56 | 53/62 |
| Body | 14/19 | 15/20 | 16/21 | **17/22** | 19/24 | 21/26 | 23/29 | 28/34 | 33/40 | 40/48 | 47/56 | 53/62 |
| Callout | 13/18 | 14/19 | 15/20 | **16/21** | 18/23 | 20/25 | 22/28 | 26/32 | 32/39 | 38/46 | 44/52 | 51/60 |
| Subhead | 12/16 | 13/18 | 14/19 | **15/20** | 17/22 | 19/24 | 21/28 | 25/31 | 30/37 | 36/43 | 42/50 | 49/58 |
| Footnote | 12/16 | 12/16 | 12/16 | **13/18** | 15/20 | 17/22 | 19/24 | 23/29 | 27/33 | 33/40 | 38/46 | 44/52 |
| Caption 1 | 11/13 | 11/13 | 11/13 | **12/16** | 14/19 | 16/21 | 18/23 | 22/28 | 26/32 | 32/39 | 37/44 | 43/51 |
| Caption 2 | 11/13 | 11/13 | 11/13 | **11/13** | 13/18 | 15/20 | 17/22 | 20/25 | 24/30 | 29/35 | 34/41 | 40/48 |

**SF Pro tracking (iOS/iPadOS), size pt → tracking pt**
6 +0.24 · 7 +0.23 · 8 +0.21 · 9 +0.17 · 10 +0.12 · 11 +0.06 · 12 0 · 13 −0.08 · 14 −0.15 · 15 −0.23 · 16 −0.31 · 17 −0.43 · 18 −0.44 · 19 −0.45 · 20 −0.45 · 21 −0.36 · 22 −0.26 · 23 −0.10 · 24 +0.07 · 25 +0.15 · 26 +0.22 · 27 +0.29 · 28 +0.38 · 29–30 +0.40 · 31 +0.39 · 32 +0.41 · 33–34 +0.40 · 36 +0.37 · 40 +0.37 · 44 +0.37 · 48 +0.35 · 52 +0.33 · 56 +0.30 · 60 +0.26 · 64 +0.22 · 68 +0.17 · 72 +0.14 · 76 +0.07 · 80+ 0.
SF Pro Rounded and New York have their own tables (Rounded is looser, e.g. 17 pt → +0.37; New York tightens with size, e.g. 17 pt → −0.07, 34 pt → −0.45) — see the source page.

## Writing
Source: https://developer.apple.com/design/human-interface-guidelines/writing

**Getting started**
- Define the app's voice (who you're talking to, how they should feel); keep a glossary of terms for consistency.
- Vary tone by context — serious for errors and payments, light for celebrations.
- Be clear and brief; cut every unnecessary word; read it aloud.
- Write for everyone: plain language, no jargon or gendered terms, localization-ready.

**Best practices**
- Most important info first; split multiple ideas across screens.
- Action-oriented labels: verbs on buttons ("Send", not "Let's do it!"). Links describe their destination — never "Click here".
- Pick a capitalization style per element type (title case vs. sentence case) and apply it everywhere.
- Multi-step flows: start with "Get Started", move with consistent "Continue"/"Next" (or hint the next step), end with "Done".
- Use possessives sparingly ("Favorites", not "Your Favorites"); don't mix perspectives; avoid "we" ("Unable to load content", not "We're having trouble…").
- Use device-correct verbs: "tap" on iPhone/iPad, not "click". Small screens need brevity.
- Empty states: welcome, explain, and offer a button/link to the next action; don't put crucial info there.
- Errors: prevent them first; show next to the problem; no blame; say how to fix ("Choose a password with at least 8 characters", not "That password is too short"); skip "Oops!". Frequent errors signal a design problem.
- Pick the right channel for the message's urgency (notification vs. alert vs. action sheet).
- Settings labels: plain; describe what the ON state does. Link directly to a setting instead of describing its location.
- Text fields: clear labels, placeholder hints showing format ("name@example.com"); inline, instructive errors ("Use only letters for your name", not "Invalid name").
