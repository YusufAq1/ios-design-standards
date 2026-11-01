# Patterns

Summarized from Apple's Human Interface Guidelines (iOS and iPadOS guidance only). Paraphrased; exact specs kept. Open the source link for Apple's exact wording.

## Charting data
Source: https://developer.apple.com/design/human-interface-guidelines/charting-data

- Use a chart to highlight something meaningful about data (trends, current state, comparisons). If people just need the data, a sortable/searchable list or table may be better.
- Keep charts simple; reveal detail progressively (levels of detail, subsets, increasingly capable versions).
- Every chart must be accessible: accessibility labels for values and components, plus accessibility elements for interaction. A text summary helps but doesn't replace labels.
- Prefer familiar types (bar, line). Novel charts need a built-in explanation (like Activity animating each ring).
- Look at the data from macro (totals, averages), mid (subsets) and micro (single points) levels to find what to surface.
- Add titles, subtitles, annotations and a headline summary ("Chance of light rain in the next hour").
- Size to function: big enough for labels and interaction; small charts for glanceable previews.
- Keep similar charts consistent; vary only to highlight real differences. Multiple views of the same dataset share type, colors, annotations and layout.

## Collaboration and sharing
Source: https://developer.apple.com/design/human-interface-guidelines/collaboration-and-sharing

- Use system share sheet and Messages integration (works with CloudKit, iCloud Drive or custom backends — custom needs universal links). SharePlay covers real-time shared activities.
- Put the Share button somewhere convenient (toolbar). SwiftUI: `ShareLink`.
- Customize the share sheet only to offer your supported sharing types ("send copy" vs. collaborate).
- Write short permission summaries ("Only invited people can edit", "Everyone can make changes").
- Keep sharing options few and grouped (who can access, edit vs. read, can collaborators invite others).
- Show the system Collaboration button prominently, next to Share, as soon as collaboration starts.
- Collaboration popover: collaborators + Messages/FaceTime at top, your custom items in the middle (only essentials, e.g. recent changes), manage button at the bottom ("Manage Shared File" by default; rename if apt).
- Post collaboration events (edits, membership changes, mentions) to Messages with a universal link (`SWHighlightEvent`).

## Drag and drop
Source: https://developer.apple.com/design/human-interface-guidelines/drag-and-drop

Default: same container → move; different container → copy; between apps → always copy. On iOS/iPadOS it works by touch, pointer and Full Keyboard Access; Universal Control drags between Mac and iPad.

**Best practices**
- Support it broadly — people try it everywhere (system text fields/views include it).
- Always offer an alternative (menu commands, accessibility drag/drop descriptors).
- Pick move vs. copy by what people expect; choose the option least likely to lose data.
- Support multi-item drags. **iPadOS:** let people add items to a drag in progress, show flocking, accept multiple simultaneous drops.
- Make drops undoable; confirm drops that can't be undone; or offer a way to reverse.
- Offer multiple representations, highest fidelity first (PDF → PNG → JPEG; native object → image).
- Consider spring loading (hovering a drag over a button/segment activates it on iPad).

**Feedback**
- Show a translucent drag image after about **3 points** of movement; keep it until drop.
- Adapt the drag image to preview the result if helpful (e.g. final size); use flocking for groups; avoid constant radical changes.
- Highlight valid destinations only while hovering; show nothing or `circle.slash` for invalid ones; one destination highlighted at a time.
- Failed/invalid drop: animate back to source, or scale-and-fade.

**Accepting drops**
- Auto-scroll scrolling destinations while dragging within them.
- Take the richest representation you support; extract only the relevant part (Mail takes name + email from a contact).
- With a hardware keyboard, Option at drop time forces copy within the same container.
- Show progress (and a placeholder in lists/collections) for slow transfers; show progress for drops that start a task (e.g. printing).
- Keep the source's text style if both sides support it; otherwise apply destination style.
- Keep dropped content selected in the destination; deselect it in the source.

## Entering data
Source: https://developer.apple.com/design/human-interface-guidelines/entering-data

- Don't ask for what the system can supply (settings, or with permission: location, calendar).
- Make the requested data clear: placeholder prompts ("username@company.com"), labels ("Email"), sensible prefilled defaults.
- Use secure fields (`SecureField`) for sensitive input.
- **Never prefill a password field** — require entry, biometrics or Keychain.
- Prefer choices (pickers, menus) to typing.
- Support paste and drag and drop as input.
- Validate as people type and flag problems immediately; use number formatters for numeric fields (decimals, percent, currency).
- Disable Next/Continue until required fields are filled.

## Feedback
Source: https://developer.apple.com/design/human-interface-guidelines/feedback

Feedback covers status, success/failure, warnings and chances to fix mistakes. Match delivery to significance: passive for status, interruptive for possible data loss.

- Make feedback accessible by combining channels — color, text, sound, haptics — so it reaches people with sound off, eyes elsewhere, or VoiceOver.
- Put status inline near what it describes (Mail's toolbar shows last update and unread count).
- Alerts only for critical, ideally actionable info; overuse kills their impact.
- Warn before **unexpected, irreversible** data loss; don't warn when loss is the expected outcome (deleting a file).
- Confirm completion only for significant actions (e.g. Apple Pay); otherwise only report failure.
- When a command can't run, say so and explain why.

## File management
Source: https://developer.apple.com/design/human-interface-guidelines/file-management

- iPadOS: offer New/Open commands with keyboard shortcuts (shown in the Command-key shortcuts overlay). Always provide an Add (+) button too.
- Custom file browsers should mirror the Files app's model; open to the most relevant location but allow browsing everywhere.
- **Auto-save** periodically, on close and on app switch — don't require an explicit Save.
- Hide file extensions by default, let people show them, and reflect the choice in every open/save UI.
- Quick Look: preview files your app can't open; ship a Quick Look generator for custom file types so Files and Spotlight can preview them.

**iOS/iPadOS document launcher (iOS 18+ / iPadOS 18+, `DocumentGroupLaunchScene`)**
- Three parts: title card (app name + primary and secondary buttons), background with accessory images, and a sheet with a file browser plus optional controls.
- Primary button = most important action (usually create new); secondary = extra options (e.g. Numbers: "Start Writing" / "Choose a Template").
- Background (solid, gradient or pattern) must be clearly distinct from accessories and title card; nothing busy.
- Accessories may sit in front of and behind the card but must never obscure the name or buttons; don't clutter; test all sizes/orientations.
- Animate sparingly — gentle repeating motion (breathe, sway).

**File provider extensions**
- Show only files relevant to the requesting context (only PDFs for a PDF editor); consider dates, sizes, local/remote status.
- Let people pick a destination (and create folders) when exporting/moving.
- No custom top toolbar — the modal already has one.

## Going full screen
Source: https://developer.apple.com/design/human-interface-guidelines/going-full-screen

- Offer full screen for games, media (video, slideshows) and focused in-depth tasks.
- Adjust proportions to use extra space, but don't change which items appear and don't resize windows programmatically; keep transitions smooth.
- Keep essential controls available (e.g. playback controls persistent or easy to reveal).
- iPadOS: let people reveal the Dock (except in games).
- Pause games/slideshows when people switch away; resume where they left off.
- Never exit full screen automatically — people choose when.
- You may hide toolbars/navigation while content is the focus; restore them with a familiar tap or swipe. Keep anything essential for navigation visible.
- **iOS/iPadOS:** the Home indicator auto-hides and returns on a bottom-edge touch, with one swipe to exit. Keep that if possible; if accidental exits are a problem, defer system gestures to require two swipes (`preferredScreenEdgesDeferringSystemGestures`).

## Launching
Source: https://developer.apple.com/design/human-interface-guidelines/launching

- Launch instantly — people won't wait more than a couple of seconds.
- iOS/iPadOS **require a launch screen**.
- Splash/brand graphics belong at the start of onboarding (or right after launch if there's no onboarding), not in the launch screen.
- Restore previous state in detail on relaunch (navigation location, scroll position, window state).

**Launch screens**
- Purpose is only to make launch feel fast — not onboarding, not a splash, not art.
- Make it nearly identical to the first screen to avoid a flash; if the app first shows a solid color, the launch screen is just that color. Match current orientation and light/dark mode.
- **No text** (it can't be localized). **No ads, logos or branding** unless they're a fixed part of the first screen; don't make it look like a splash or About screen.
- **iOS/iPadOS:** launch in the device's current orientation if both are supported; single-orientation apps launch in theirs. Landscape-only apps must work in both landscape-left and landscape-right.

## Live-viewing apps
Source: https://developer.apple.com/design/human-interface-guidelines/live-viewing-apps

- Put live content first (first tab) and make it instantly distinguishable from video on demand.
- One tap (or zero) to start playback — e.g. a Watch Now button that vanishes as full-screen playback begins.
- Mark live items (a "Live" row, badges, symbols, sashes); show progress for in-progress live programs.
- Playback is always the primary action; secondary actions (Start Over, Record, Download, Favorite) appear in the same order everywhere. Show other air times.
- Content footer for browsing during playback: subtle dimming for legibility, highlight the current channel's thumbnail, use EPG categories, symmetric invoke/dismiss gestures.
- Instant visual feedback on channel change. Audio follows context: keep it while browsing within live, stop it when leaving the live tab.
- **EPG:** current program/channel/time obvious with a quick way back; easy paging/jumping; My Channels/Favorites; familiar categories (Movies, TV Shows, Kids, Sports, Popular); browse while playback continues (PiP or background).
- **Cloud DVR:** record from the info panel during live viewing; record future programs from a details view (this episode vs. series); fine-grained options (new episodes only, specific teams); play/delete/adjust from DVR details; storage management settings (auto-delete watched or old recordings).

## Loading
Source: https://developer.apple.com/design/human-interface-guidelines/loading

- Show something immediately — placeholders, skeletons or animation that content replaces as it arrives. A blank screen looks broken.
- Let people do other things while content loads in the background.
- For unavoidable long loads, show useful filler (tips, hints, new features) sized to the real wait.
- Download large assets in the background after install/update (Background Assets framework).
- Use determinate progress indicators when duration is known, indeterminate when not. Games may use custom on-brand loading views.

## Managing accounts
Source: https://developer.apple.com/design/human-interface-guidelines/managing-accounts

- Require an account only if core functionality needs it. If required, consider Sign in with Apple.
- Explain briefly why an account is needed and its benefits, in the sign-in view.
- **Delay sign-in** as long as possible (e.g. browse freely, sign in to purchase).
- Without Sign in with Apple, prefer **passkeys**; if passwords remain, require two-factor authentication.
- Name the method on the button ("Sign In with Face ID", not "Sign In"); mention only methods the device has (`LABiometryType`).
- Don't add an in-app toggle for biometrics (it's a system setting). Don't call account credentials a "passcode".

**Deleting accounts** (required if you let people create one)
- Offer true deletion, not just deactivation; comply with local law (right to be forgotten). If law requires retaining data, explain what and why.
- Start deletion inside the app, or give a direct, easy-to-find link to the web page that does it (not buried in the privacy policy or terms).
- Same effort in-app and on the web. Sign in with Apple accounts: revoke tokens on deletion.
- Optionally allow scheduled deletion, but always offer immediate deletion too.
- Say when deletion will complete and notify when it's done.
- With in-app purchases, explain that Apple keeps billing auto-renewing subscriptions until the person cancels, and how to cancel or request a refund. Deletion must be supported even if the subscription was bought elsewhere.

**TV provider accounts:** use TV Provider Authentication; don't show sign-out when signed in at system level (direct to Settings › TV Provider); never tell people to sign out via privacy controls.

## Managing notifications
Source: https://developer.apple.com/design/human-interface-guidelines/managing-notifications

- Permission is required before sending any notification; people can change it in Settings.
- Support Focus and scheduled summaries. Messaging/calls use **communication notifications** (adopt SiriKit intents); everything else is noncommunication and needs an interruption level.

| Interruption level | Use for | Overrides scheduled summary | Breaks through Focus | Overrides Ring/Silent |
|---|---|---|---|---|
| Passive | View-whenever info (a recommendation) | No | No | No |
| Active (default) | Good to know now (a score update) | No | No | No |
| Time Sensitive | Needs attention now (security issue, delivery) | Yes | Yes | No |
| Critical | Urgent health/safety; requires an entitlement | Yes | Yes | Yes |

- Assign levels honestly — overstated urgency gets your notifications turned off.
- Time Sensitive only for events happening now or within an hour; the system explains it and lets people turn it off.
- **Marketing notifications:** only with explicit opt-in via your own UI explaining what you'll send; **never Time Sensitive**; provide in-app settings to change notification choices.

## Modality
Source: https://developer.apple.com/design/human-interface-guidelines/modality

Use modality to deliver critical info, confirm/modify an action, run a narrow self-contained task, or focus on immersive/complex work. iOS/iPadOS tools: alerts, action sheets, activity views, sheets, popovers, full-screen modals (iPadOS can also use separate windows).

- Only use modal presentation when it clearly helps.
- Keep modal tasks short and simple. Don't build an app-within-the-app; if subviews are needed, one path through them, and no buttons that look like the dismiss button.
- Full-screen modal for media, camera, or multi-step editing/markup.
- Always provide an obvious dismissal — on iOS/iPadOS, a button in the top toolbar or swipe down.
- If dismissing would lose user content, confirm first (iOS: action sheet with a save option).
- Title the modal with its task; add guidance text if needed.
- Dismiss one modal before presenting another. Alerts may appear above everything, but **never more than one alert at a time**.

## Multitasking
Source: https://developer.apple.com/design/human-interface-guidelines/multitasking

Every app (except some games) must work well with multitasking; you can't know when it starts, so always be ready to save and restore context.

- Pause anything needing attention (games, media) when people switch away; resume seamlessly.
- Audio interruptions: pause indefinitely for primary interruptions (music, podcasts, audiobooks); duck or pause briefly for short ones (GPS prompts) and restore afterward.
- Finish user-started tasks (downloads, video processing) in the background.
- Notify on completion only for important/time-sensitive tasks, not routine ones.
- **iOS:** Picture in Picture for video and FaceTime while using other apps.
- **iPadOS:** multiple apps and multiple windows per app; full-screen or windowed mode with resizable windows, tiling, minimize and close controls (frontmost window has colored controls and casts a shadow); PiP above everything. Apps aren't told the configuration — adapt to any size (see Layout, Windows).

## Offering help
Source: https://developer.apple.com/design/human-interface-guidelines/offering-help

- Match help to the task: inline explanations for 1–2-step tasks, tutorials for complex ones. Tie help to what people are doing now; make it easy to dismiss.
- Use context-correct language and images (tap vs. click; the right input device). Keep help inclusive.
- Don't explain standard components; explain what they do in your app. For unusual controls or input, orient quickly with animation/graphics rather than long text.

**Tips (TipKit)**
- Popover tip to preserve content flow; inline tip to keep surroundings visible (annotation style points at a UI element; hint style for general features).
- Only for simple features — **more than three actions is too complex for a tip**.
- One or two sentences, direct and actionable; no promotion or unrelated content.
- Use eligibility rules (parameters/events) so tips reach only people who'll benefit (not those already using the feature); throttle multiple tips (e.g. **once every 24 hours**).
- Include the associated symbol (prefer filled), unless the tip points directly at that same image in the UI.
- Add buttons to jump to settings or deeper resources.

## Onboarding
Source: https://developer.apple.com/design/human-interface-guidelines/onboarding

Happens after launch, not during it. Fast, fun, optional.

- Teach by doing — let people safely try the action or mechanic.
- Prefer contextual tips near the relevant UI over one big up-front flow.
- Required flows must be brief and not demand memorization.
- Tutorials should be skippable; once skipped, don't re-show on launch, but keep it findable (help, account or settings).
- Teach your app, not the device or OS.
- Splash screen, if any: brief, glanceable.
- Ship enough content in the bundle so people needn't wait for downloads.
- Leave licenses and disclaimers to the App Store page; if unavoidable, integrate without disrupting.
- Postpone nonessential setup; use good defaults.
- Ask for permissions during onboarding only if the app can't work without them (and explain the benefit); otherwise ask at first use.
- Let people experience the app before asking for ratings or purchases.

## Playing audio
Source: https://developer.apple.com/design/human-interface-guidelines/playing-audio

Expectations: **Silent mode** plays only audio people explicitly start (media, alarms, calls) — silence keyboard clicks, sound effects, soundtracks. **Volume** controls apply to all sound (ringer volume is separate). **Headphones**: connecting reroutes seamlessly; disconnecting **pauses playback immediately**.

- Balance relative levels inside your mix; never change system volume.
- Allow output rerouting (AirPlay, Bluetooth) unless there's a strong reason not to.
- Use the system volume view (`MPVolumeView`, slider + route picker; slider appearance customizable).
- Choose the right audio session category:

| Category | Use when | Silent switch | Mixes with others | Background |
|---|---|---|---|---|
| Solo ambient | Nonessential sound that silences others (game soundtrack) | Obeys | No | No |
| Ambient | Nonessential sound that mixes (game where people play their own music) | Obeys | Yes | No |
| Playback | Essential sound (audiobook, language lessons) | Ignores | Optional | Yes |
| Record | Recording (voice notes) | Ignores | No | Records in background |
| Play and record | Simultaneous (voice/video calls, audio messages) | Ignores | Optional | Yes |

- Respond to remote/headphone/Control Center controls only when actively playing, in a clear audio context, or connected to Bluetooth/AirPlay — otherwise don't stop other apps' audio.
- Never repurpose standard audio controls; ignore ones you don't support.
- Custom player controls only for commands the system lacks (custom skip intervals, related content like scores).
- After temporary audio, notify others to resume (`notifyOthersOnDeactivation`).
- Interruptions: decide handling deliberately (e.g. don't auto-unmute a mic after an iPad Smart Folio closes — privacy). On interruption end, media apps resume only if the interruption is resumable; games may resume automatically.
- **iOS/iPadOS:** use System Sound Services for short sounds and vibrations.

## Playing haptics
Source: https://developer.apple.com/design/human-interface-guidelines/playing-haptics

- Standard controls (toggles, sliders, pickers) play system haptics automatically on iPhone. Some game controllers, Apple Pencil and trackpads on iPad also support haptics.
- Use system patterns only for their documented meanings; otherwise use a generic or custom pattern.
- Be consistent: each pattern maps to one kind of outcome (don't reuse a "failure" pattern for success).
- Haptics complement visuals and sound — match intensity/sharpness to the animation; sync with audio.
- Don't overuse; user-test for balance. In apps prefer short haptics for discrete events (long ones dilute meaning).
- **Make haptics optional**; the app must work fully without them.
- Make sure vibration doesn't disturb camera, gyroscope or microphone use.
- **Custom haptics (Core Haptics):** transient events (taps/impulses) and continuous events (sustained vibration), each with adjustable **intensity** and **sharpness** (soft/organic vs. crisp/mechanical), optionally with audio.
- **iOS feedback generators (`UIFeedbackGenerator`):** *Notification* (outcome of a task: success, warning, error), *Impact* (physical metaphor: snap into place, collision), *Selection* (values changing in a control).

## Playing video
Source: https://developer.apple.com/design/human-interface-guidelines/playing-video

- System player default modes: **aspect-fill** for wide video (2:1 to 2.40:1, may crop edges); **aspect-fit** for standard (4:3, 16:9, up to 2:1) and ultrawide (>2.40:1), with letterbox/pillarbox. Picture in Picture supported.
- Use the system player. A custom player must mirror system behaviors closely — small differences frustrate.
- Always keep original aspect ratio; **never bake letterbox/pillarbox padding into the video** (breaks scaling and PiP).
- Add metadata (image, title, description) without obscuring playback (`externalMetadata`).
- Support expected inputs (Space bar plays/pauses on a connected keyboard).
- Prevent mixed audio when switching between full screen and PiP — handle secondary audio (`silenceSecondaryAudioHintNotification`).

**TV app integration**
- Transition: TV app fades to black and skips your launch screen — show black immediately, then content.
- Start content immediately; no splash, details or intro. Rare interstitials: Select steps through, Play skips.
- Resume automatically — don't ask. Resume long videos at the previous end time.
- Switch to the requested user profile; if none specified, ask once.
- Loading: avoid loading screens; if loading exceeds **2 seconds**, black screen with a centered spinner only; start playback as soon as enough is buffered.
- On exit, show the item's detail view with a Resume option (or a relevant menu); prepare it early for immediate exits.

## Printing
Source: https://developer.apple.com/design/human-interface-guidelines/printing

- **iOS/iPadOS:** expose Print through a toolbar button that opens the action sheet (share sheet).
- Remove the Print action when nothing is printable or no printer is available; dim or hide custom print buttons.
- Use the system print options view for page range, copies, duplex, etc., when the printer supports them.

## Ratings and reviews
Source: https://developer.apple.com/design/human-interface-guidelines/ratings-and-reviews

- Ask only after demonstrated engagement (finished a level or significant task) — **never on first launch or during onboarding**.
- Ask at natural pauses, never mid-task or mid-game.
- Don't pester: leave at least **a week or two** between requests and require further engagement.
- Use the system prompt (`RequestReviewAction`): it checks for prior feedback, offers rating + optional review, is dismissible in one tap, can be disabled globally, and is **limited by the system to 3 displays per app per 365 days**.
- Resetting the summary rating on a new version reflects current quality but lowers the visible rating count — weigh it.

## Searching
Source: https://developer.apple.com/design/human-interface-guidelines/searching

- In-app search uses a search field; personalize with recent searches, suggestions, completions, corrections. Offer scopes/filters (scope bars, tokens) where useful; support find-in-page for documents.
- If search matters, give it a primary spot — bottom toolbar (Notes) or a dedicated Search tab (Photos, TV).
- One place to search everything; local "filter" searches are fine in distinct sections (Music library).
- Always show the current scope (placeholder text, scope bar, tokens, title).
- Show recent searches before typing and predictive suggestions while typing (`searchSuggestions`).
- Search history is private: think about who might see it and let people clear it.
- **Spotlight:** index your content with descriptive metadata; ship a Spotlight importer for custom file types (`CSImportExtension`); you can launch a Spotlight search from your UI and show results in a custom view; prefer system open/save views (built-in search); ship a Quick Look generator for custom file types.

## Settings
Source: https://developer.apple.com/design/human-interface-guidelines/settings

- Choose defaults that work best for most people (e.g. auto-tune graphics for the device) so no setup is needed.
- Offer as few settings as possible.
- Open settings the expected way — Command-Comma with a hardware keyboard (Esc in games).
- Don't ask for what you can detect (connected controllers, Dark Mode).
- **Never duplicate system-wide settings** (accessibility, scrolling, authentication) in your own settings.
- In-app settings area: general, rarely changed options (window configuration, save behavior, key mappings, account).
- Task-specific options (show/hide parts of a view, sort, filter) belong on the screen they affect.
- Put only the most rarely changed options in the system Settings app; consider a button that opens it directly.

## Undo and redo
Source: https://developer.apple.com/design/human-interface-guidelines/undo-and-redo

- Help people predict the result: describe it in the shake-to-undo alert; use specific labels ("Undo Typing", "Redo Bold").
- Show the result — scroll to and highlight off-screen changes so undo never seems to do nothing.
- Allow many levels of undo (everything since opening or saving); consider batch-undo for related tweaks or "revert to saved".
- Dedicated undo/redo buttons only when really needed — use the standard symbols, in a toolbar.
- **iOS/iPadOS:** don't redefine the standard gestures (three-finger swipe, shake). Alert titles are "Undo "/"Redo " + one or two words you supply ("Undo Name", "Redo Address Change").

## Workouts
Source: https://developer.apple.com/design/human-interface-guidelines/workouts

Applies to iPhone/iPad workouts too (walking, wheelchair pushing, running; live/recorded sessions on iPad).
- Show only data that matters during a workout (time elapsed/remaining, calories, distance) plus relevant controls (laps, intervals); hide everything else.
- Make an active workout recognizable at a glance (live-updating metrics, distinctive layout).
- Pause/resume/stop must be easy to find and tap; clearly confirm start and stop.
- When sensors can't measure (water and heart rate), explain what's still tracked, in language like the Workout app's.
- Finish with a summary (consider Activity rings). Discard or ask about sessions that last only seconds.
- Text legible in motion: large sizes, high contrast, key info prominent.
- Use Activity rings only for their documented meaning.
