---
name: ios-design-standards
description: Apple design and App Store standards for iPhone and iPad apps — Human Interface Guidelines (iOS/iPadOS), App Store Review Guidelines, and App Store asset specs. Use whenever designing, building, reviewing or critiquing an iOS or iPadOS app or screen (SwiftUI, UIKit, Figma mockups, wireframes), choosing components, writing UI copy or permission prompts, planning monetization/sign-in/privacy flows, or preparing an App Store submission, screenshots, previews or product page.
---

# iOS design standards

A condensed, iOS- and iPadOS-focused digest of Apple's design and App Store rules, with exact specs (sizes, limits, contrast ratios) and a source link for every page. Use it to design to the standard up front and to audit existing work.

The references are paraphrased summaries, not Apple's text. When exact wording matters, or before an App Store submission, open the `Source:` link in the relevant section — Apple updates these pages, especially the App Review Guidelines and screenshot sizes.

## How to use this skill

1. **Identify what's being designed** — a screen, a flow (onboarding, sign-in, purchase, permissions), a component choice, copy, or App Store material.
2. **Load only the reference files you need** (table below). Search within a file by the `## Page name` heading rather than reading every file.
3. **Apply the rules**, preferring system components and behaviors over custom ones.
4. **When reviewing**, report findings as: what's wrong → the rule (with its source page or guideline number) → a concrete fix. Mark each **Must fix** (App Review rejection risk, accessibility failure, broken platform behavior) or **Should fix** (HIG best practice).
5. **For anything shipping to the App Store**, also check `07-app-store-review.md` and `08-app-store-assets.md`.

## Reference files

| File | Covers |
|---|---|
| `references/01-platforms.md` | Design principles; Designing for iOS, iPhone Duo (two-display iPhone), iPadOS |
| `references/02-foundations.md` | Accessibility, app icons, branding, color, Dark Mode, icons + standard SF Symbols, images, inclusion, layout & size classes, materials/Liquid Glass, motion, privacy & permission prompts, right-to-left, SF Symbols, typography + full Dynamic Type tables, writing (immersive experiences and spatial layout are visionOS-only) |
| `references/03-patterns.md` | Charting data, collaboration & sharing, drag and drop, entering data, feedback, file management, full screen, launching & launch screens, live viewing, loading, managing accounts & account deletion, notifications & interruption levels, modality, multitasking, help & tips, onboarding, audio, haptics, video, printing, ratings & reviews, searching, settings, undo/redo, workouts |
| `references/04-components.md` | Content (charts, image/text/web views) · Layout (boxes, collections, disclosure, labels, lists & tables, split views) · Menus & actions (share sheet, buttons, context/edit menus, quick actions, menus, pop-up/pull-down buttons, iPad menu bar, toolbars) · Navigation (search fields, sidebars, tab bars) · Presentation (action sheets, alerts, page controls, popovers, scroll views, sheets, iPad windows) · Selection & input (color wells, pickers, segmented controls, sliders, steppers, text fields, toggles, keyboards) · Status (Activity rings, gauges, progress) · System experiences (App Shortcuts, Controls, Live Activities, notifications, snippets, status bar, widgets + size tables) |
| `references/05-inputs.md` | Action button, Apple Pencil & Scribble, Camera Control, iPad focus & keyboard navigation, game controls & touch controls, gestures, motion sensors, hardware keyboard shortcuts, nearby interactions, iPad pointer |
| `references/06-technologies.md` | AirPlay, Always On, App Clips (+ App Clip Codes), In-App Purchase & subscriptions, Apple Pay, AR, CareKit, CarPlay, Game Center, generative AI, HealthKit, HomeKit, iCloud, ID Verifier, iMessage apps & stickers, Live Photos, Mac Catalyst, machine learning, Maps, NFC, photo editing, ResearchKit, SharePlay, ShazamKit, Sign in with Apple, Siri, Tap to Pay, VoiceOver, Wallet |
| `references/07-app-store-review.md` | App Review Guidelines 1–5 by number (safety, performance, business/payments, design, legal/privacy), before/after you submit, plus App Review help pages (complete-review info, device testing, IAP sandbox, screenshots rule, purpose strings, account deletion, kids & age ratings) |
| `references/08-app-store-assets.md` | Asset best practices, screenshot/app preview/creative asset specs, In-App Events, product page metadata limits, custom product pages, product page optimization, discovery, App Store marketing & trademark rules |
| `references/00-index.md` | Every source page → which file and heading covers it |

## Always-check list (most common problems)

Run through these for any iOS/iPadOS screen or flow before going deeper:

**Layout and adaptivity**
- Layout driven by **size classes**, not device type or orientation; works on every iPhone size, iPad split view/windowed sizes, and iPhone Duo; content inside **safe areas**. (Foundations › Layout; Platforms › iPhone Duo)
- Works with **Dynamic Type up to AX5** — text wraps, rows grow, side-by-side items stack; no clipped text. (Foundations › Typography)
- Supports **Dark Mode** and **Increase Contrast** using semantic system colors; no app-specific light/dark toggle. (Foundations › Color, Dark Mode)
- Controls float on **Liquid Glass**; no solid backgrounds under bars — use scroll edge effects; Liquid Glass never used in the content layer. (Foundations › Materials; Components › Toolbars)

**Accessibility**
- Tap targets **≥44×44 pt** (absolute minimum 28×28 pt); about 12 pt spacing around bezeled controls.
- Text contrast **≥4.5:1** (≥3:1 for 18 pt+ or bold); color never the only signal.
- Default body **17 pt**, nothing under **11 pt**.
- Every control and meaningful image has a **VoiceOver label**; decorative images hidden; every gesture has an onscreen alternative; honors **Reduce Motion**.

**Navigation and components**
- **Tab bar** for top-level sections only (never actions); tabs never hidden or disabled; avoid "More" overflow. Toolbars for actions; one prominent (primary) action on the trailing side; standard Back/Close symbols (no "Back" text).
- Sheets: Cancel leading / Done trailing; swipe to dismiss with a confirm if there are unsaved changes; one sheet at a time. No popovers in compact width.
- Alerts only for critical, actionable info; **never at launch**; ≤3 buttons; "Cancel" for cancel; destructive style only for unintended destruction. Choices after a deliberate action → action sheet.
- Switch toggles only in list rows. Segmented controls ≤5 segments on iPhone. Never a slider for volume.

**Copy**
- Verbs on buttons; title case for menus/buttons/tab labels as the components specify; "tap" not "click"; no "we" in errors; errors say how to fix.
- Purpose strings: one specific, active-voice sentence ending in a period that says exactly how data is used — localized.

**Privacy, accounts and money** (App Review hot spots)
- Ask for permissions **in context**, not at launch; pre-permission screens have one "Continue"/"Next" button; no ATT incentives or fake alerts. (Foundations › Privacy; Guideline 5.1)
- Let people use the app **without an account** unless it's core; if accounts exist, **in-app account deletion** is required. Third-party login for the primary account → also offer Sign in with Apple-equivalent login. (Guidelines 4.8, 5.1.1(v))
- **Digital goods → In-App Purchase**; physical goods/services → Apple Pay or other methods. Show full billing price, period, trial terms, restore purchases, Terms & Privacy links on paywalls; cancelling must be easy. (Guidelines 3.1; Technologies › In-App Purchase)
- Privacy policy linked in-app and in App Store Connect; no tracking without ATT; nothing gated on enabling notifications/location/tracking.
- Push notifications not required to use the app; marketing pushes only with explicit opt-in.

**App Store submission**
- Demo account (or approved demo mode), live backend, specific review notes; no placeholder content; works on iPad in compatibility mode; IPv6.
- Screenshots: required sizes (iPhone 6.3"/Dynamic Island medium **1206×2622** or **1179×2556**; iPad 13" **2064×2752** or **2048×2732**), **more than half show the app in use**, no prices/URLs/other platforms/Apple awards, 4+ appropriate. App name and subtitle **≤30 characters**, keywords **100 characters**, promotional text **170 characters**.

## Scope notes

- Covers iOS and iPadOS only. watchOS, tvOS, macOS and visionOS sections of each page were left out; pages that apply only to those platforms are listed with a "Not supported on iOS or iPadOS" note so nothing silently disappears.
- External API docs, sample code and WWDC videos linked from these pages are not summarized — follow their links when implementation detail is needed.
- This is an unofficial digest. Apple's live pages always win if they differ.
