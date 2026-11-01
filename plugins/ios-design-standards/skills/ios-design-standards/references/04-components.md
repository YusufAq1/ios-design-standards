# Components

Summarized from Apple's Human Interface Guidelines (iOS and iPadOS guidance only). Paraphrased; exact specs kept. Open the source link for Apple's exact wording. Grouped as on Apple's site: Content · Layout and organization · Menus and actions · Navigation and search · Presentation · Selection and input · Status · System experiences.

---
# Content
Overview: https://developer.apple.com/design/human-interface-guidelines/content

## Charts
Source: https://developer.apple.com/design/human-interface-guidelines/charts

**Anatomy:** marks (bar, line, point…) plotted in a plot area via scales; axes with ticks and grid lines; labels, titles, subtitles, annotations, legends; accessibility labels. Build with Swift Charts.

**Marks**
- Bar: compare categories, parts of a whole, or per-period totals (daily steps).
- Line: change over time and trends.
- Point: individual values, relationships between two properties, outliers and clusters.
- Combine (points on a line) when it adds clarity.

**Axes**
- Fixed range when bounds are meaningful (battery 0–100%); dynamic range when values vary widely (Health steps).
- Bars usually start at zero; don't force zero when it hides meaningful differences (heart rate).
- Use familiar tick sequences (0, 5, 10 — not 1, 6, 11).
- Tune grid line density/weight to the use case; lighter when people can inspect points interactively.

**Descriptions**
- Titles/labels explain the chart's purpose before people dig in (critical for VoiceOver and cognitive accessibility).
- Summarize the main message up front (Weather's precipitation title/subtitle).

**Best practices**
- Data most prominent; axes and descriptions support without competing.
- Compact widths: maximize plot width; keep Y-axis labels short; move units to the title; put long category labels inside the plot if they don't obscure data.
- Fully accessible: accessibility labels + Audio Graphs.
- Interaction is optional — never required to see critical info (Stocks' scrubbable line).
- Small marks: make the whole plot area the hit target and allow scrubbing.
- Keyboard/Switch Control: define a logical navigation path (e.g. along the X axis) or let focus move between subsets for big datasets.
- Announce important changes to marks/axes, not just animate them (accessibility notifications).
- Align the chart's leading edge with other views; grid-line labels on the trailing side; consider the Y axis on the trailing side.

**Color**
- Never color alone — add shapes or patterns (Health uses different point shapes for systolic/diastolic).
- Add separators between adjacent color areas (stacked bars).

**Chart accessibility**
- Swift Charts gives default Audio Graphs and per-mark elements; customize with a title and summary. Without Audio Graphs, describe chart type, what each axis means and the bounds.
- Label each important/interactive element, or groups of marks — whichever matches the chart's purpose (Maps summarizes elevation by segment; Health labels every bar). Small preview charts can use one high-level label.
- Labels: context first (date/location), then value; no subjective words ("rapidly", "almost") — use actual values; unambiguous formats ("June 6" not "6/6", "60 minutes" not "60m"); say what series *represent*, not their colors; mention axes in a consistent order.
- Hide visible axis/tick labels from assistive tech.

## Image views
Source: https://developer.apple.com/design/human-interface-guidelines/image-views

- For displaying an image (or animated sequence); generally non-interactive. For a tappable image, use a system button configured with the image.
- For icons use SF Symbols or template interface icons, not image views — they take accent colors.
- Text over images hurts both: ensure contrast; add shadow or background layer.
- Keep all frames of an animated sequence the same size; prescale to the view for performance.

## Text views
Source: https://developer.apple.com/design/human-interface-guidelines/text-views

- For long, editable, or specially formatted multiline text (scrolls; leading-aligned; system label color by default). Short text → label; short editable → text field.
- Keep text legible; adopt Dynamic Type; test with Bold Text and other accessibility settings.
- Make useful text selectable (error messages, serial numbers, IP addresses).
- **iOS/iPadOS:** show the keyboard type that matches the content.

## Web views
Source: https://developer.apple.com/design/human-interface-guidelines/web-views

- Embed web content (e.g. HTML email) in context.
- If people may visit several pages, enable back/forward navigation and provide the controls (off by default).
- **Don't build a web browser** with a web view — Safari is for browsing.

---
# Layout and organization
Overview: https://developer.apple.com/design/human-interface-guidelines/layout-and-organization

## Boxes
Source: https://developer.apple.com/design/human-interface-guidelines/boxes

- Group related info with a border or background; keep boxes small relative to their container.
- Use padding/alignment for sub-grouping instead of nested boxes.
- Optional short title in sentence case, no ending punctuation (colon only in settings panes); helps VoiceOver.
- **iOS/iPadOS:** boxes use the secondary and tertiary background colors by default.

## Collections
Source: https://developer.apple.com/design/human-interface-guidelines/collections

- Best for image-based content. Use the standard row or grid layout; avoid attention-seeking custom layouts.
- Text content → use a list/table instead.
- Easy selection: enough padding so focus/hover effects are visible and items don't overlap.
- Defaults: tap selects, touch-and-hold edits, swipe scrolls; add gestures only if needed.
- Animate inserts, deletes and reorders.
- **iOS/iPadOS:** avoid changing layout dynamically while people are interacting, unless they asked for it.

## Column views
Source: https://developer.apple.com/design/human-interface-guidelines/column-views

**Not supported on iOS or iPadOS** (macOS only, like Finder's column view). On iPad use a split view for hierarchies.

## Disclosure controls
Source: https://developer.apple.com/design/human-interface-guidelines/disclosure-controls

- Hide advanced details until relevant; keep the most-used controls visible at the top.
- **Disclosure triangle:** points toward content (trailing) when collapsed, down when expanded; give it a descriptive label ("Advanced Options").
- **Disclosure button:** points down when collapsed, up when expanded; place it next to the content it reveals; **at most one per view**.
- **iOS/iPadOS:** available via SwiftUI `DisclosureGroup`.

## Labels
Source: https://developer.apple.com/design/human-interface-guidelines/labels

- Static, non-editable (often copyable) text in buttons, lists and views. SwiftUI: `Label`, `Text`. Editable short text → text field; long text → text view.
- Prefer system fonts (Dynamic Type by default); custom styles must stay legible.
- Use label colors for importance: `label` (primary), `secondaryLabel` (subheading/supplemental), `tertiaryLabel` (unavailable item/behavior), `quaternaryLabel` (watermark).
- Make useful label text selectable (errors, locations, IP addresses).

## Lists and tables
Source: https://developer.apple.com/design/human-interface-guidelines/lists-and-tables

- Best format for text: easy to scan. Widely varying item sizes or many images → collection.
- Allow editing where it helps (reordering even if adding/removing isn't possible). On iOS/iPadOS, selection of multiple rows requires edit mode.
- Selection feedback: navigation lists keep the selected row highlighted to show the path; option lists flash the highlight, then show a checkmark.
- Keep row text short; for long content show titles only and open a detail view.
- In narrow/resizable tables, consider a middle ellipsis to keep beginning and end visible.
- Multicolumn headings: nouns/short noun phrases, title case, no ending punctuation. Single-column without a heading: give context with a label or header.
- Pick a style that fits the data: **iOS/iPadOS grouped style** uses headers, footers and spacing for groups (`ListStyle`). Use built-in row layouts (`UIListContentConfiguration`).
- **iOS/iPadOS:** the info (detail disclosure) button only reveals more info about a row — it doesn't navigate. Use a **disclosure indicator** (chevron) to drill down. Don't add an alphabetical index to a list whose rows have trailing controls like disclosure indicators (they collide).

## Lockups
Source: https://developer.apple.com/design/human-interface-guidelines/lockups

**Not supported on iOS or iPadOS** (tvOS: cards, caption buttons, monograms, posters).

## Outline views
Source: https://developer.apple.com/design/human-interface-guidelines/outline-views

**Not supported on iOS or iPadOS** (macOS). On iPad use lists with disclosure groups / sidebars.

## Split views
Source: https://developer.apple.com/design/human-interface-guidelines/split-views

- Show multiple hierarchy levels side by side: primary (often a sidebar) → secondary → optional tertiary pane. Rarely, panes hold supplementary tools (inspector).
- Persistently highlight the current selection in every pane leading to the detail.
- Support drag and drop between panes.
- **iOS:** use only in regular-width environments — not on iPhone portrait (compact).
- **iPadOS:** two panes (Mail) or three (Keynote). Windows resize fluidly — design for narrow, compact and intermediate widths so pane navigation stays logical (`NavigationSplitView`, `UISplitViewController`).

## Tab views
Source: https://developer.apple.com/design/human-interface-guidelines/tab-views

**Not supported on iOS or iPadOS** (macOS tabbed panes). On iOS/iPadOS use a **segmented control** for similar switching within a view. (App-level navigation uses a tab bar — see Navigation and search.)

---
# Menus and actions
Overview: https://developer.apple.com/design/human-interface-guidelines/menus-and-actions

## Activity views (share sheet)
Source: https://developer.apple.com/design/human-interface-guidelines/activity-views

- Shows sharing targets, actions (Copy, Print…) and frequent apps; opened from the Share button; appears as a sheet or popover depending on device/orientation. App-specific actions list before system ones; people can edit the list.
- Don't duplicate system actions (no second Print). Similar but custom functions get a specific title ("Print Transaction").
- Use an SF Symbol for custom activities; custom icons centered in about **70×70 px**.
- Action titles: a verb or short verb phrase; no company/product name (share activities show the company name under the icon automatically).
- Exclude irrelevant system activities; show custom ones only when applicable.
- Always open it with the standard Share button; no alternative entry points for the same thing.

**Share and action extensions** (appear in the share sheet on iOS/iPadOS)
- Share extensions: prefer the system compose view. Action extensions: include your app name and app-like UI elements.
- Keep interaction minimal — ideally one tap.
- No extra modal views over the extension (an alert is OK).
- Share extensions use your app icon automatically; action extensions use a symbol/icon that names the task.
- Long tasks continue in the background with status in the main app; notify only on problems, not completion.

## Buttons
Source: https://developer.apple.com/design/human-interface-guidelines/buttons

A button = style + content (symbol, text or both) + role.

- **Hit region at least 44×44 pt**; enough space to tell buttons apart.
- Custom buttons must have a pressed state.
- **Style:** prominent (accent-colored background) for the most likely action — **only one or two prominent buttons per view**. Distinguish the preferred option by style, not size; keep a set of options the same size. Don't color button labels like a colorful content background — use the monochrome default.
- **Content:** make purpose obvious; use familiar symbols for familiar actions (`square.and.arrow.up` = share; see Icons standard list). Use text when clearer: a few words, title case, start with a verb ("Add to Cart").
- **Roles:** normal, primary (default; accent color; responds to Return and can auto-close sheets/alerts), cancel, destructive (system red). **Never give a destructive action the primary role**, even if it's most likely.
- **iOS/iPadOS:** for actions that don't finish instantly, show an activity indicator inside the button, optionally with an alternate label ("Checkout" → "Checking out…").

## Context menus
Source: https://developer.apple.com/design/human-interface-guidelines/context-menus

Revealed by touch and hold on iOS/iPadOS (or secondary click / Control-click with trackpad or mouse on iPad). Hidden by default, so never the only way in.

- Include only the most relevant, likely commands for that item — not advanced or rare ones. Keep it short.
- Support context menus consistently across the app.
- Every context menu command must also exist in the main UI (e.g. the message toolbar).
- Submenus: at most one level, with a predictive title.
- **Hide** unavailable items (don't dim).
- Most-used items nearest the touch point; reverse order if the menu opens above the content.
- No keyboard shortcuts in context menus.
- Separators: about **three groups max**.
- Destructive items (Delete, Remove) go **last** and are marked destructive (shown in red).
- Usually no title; add one only if it clarifies scope (e.g. "3 Messages").
- Use the system's standard icons for standard actions.
- **iOS/iPadOS:** provide a context menu **or** an edit menu for an item, never both. iPadOS: context menu in empty space can create new objects (Files → New Folder). Show a graphical preview that confirms the target (condensed message/note); match the preview's clipping path to its shape so corners don't jump during animation.

## Dock menus
Source: https://developer.apple.com/design/human-interface-guidelines/dock-menus

**Not supported on iOS or iPadOS** (macOS). The iOS/iPadOS equivalent is Home Screen quick actions.

## Edit menus
Source: https://developer.apple.com/design/human-interface-guidelines/edit-menus

- iOS: compact horizontal bar after touch-and-hold or double-tap to select; a trailing chevron expands it into a context menu. iPadOS: horizontal with touch; opens directly as a vertical context menu with keyboard/pointer. Data detectors add actions (an address → Get Directions).
- Use the system edit menu (`UIResponderStandardEditActions`); don't rebuild it.
- Reveal with standard interactions only.
- Show only applicable commands (no Copy/Cut without a selection, no Paste with an empty pasteboard).
- Put custom commands next to related system ones; don't add too many.
- Let people select and copy non-editable content text (captions, statuses) — but not control labels.
- Support undo/redo (edit commands don't confirm).
- Don't add separate controls that duplicate edit commands.
- Distinguish Delete (no pasteboard) from Cut (copies first).
- Custom labels: short verbs.
- **iOS/iPadOS:** make it work in both horizontal and vertical styles; reposition if it would cover important content (you can move it, not reshape it).

## Home Screen quick actions
Source: https://developer.apple.com/design/human-interface-guidelines/home-screen-quick-actions

- Touch and hold the app icon. Each action = title, icon (left or right depending on icon position), optional subtitle. Can update dynamically (recent conversations).
- High-value tasks only (Maps: search nearby, directions home). People expect at least one; **maximum four**.
- Dynamic changes must be predictable (location, recent activity, time of day, settings).
- Titles state the result ("Directions Home", "New Message"); subtitles add context (unread counts). No app name, no extras, short, localization-friendly.
- Use SF Symbols (or Apple's Quick Action Icon Template for custom icons). **No emoji** (they're full color; quick action icons are monochrome and adapt to Dark Mode).

## Menus
Source: https://developer.apple.com/design/human-interface-guidelines/menus

**Labels**
- Verb or verb phrase for actions (View, Close, Select); match your app's tone.
- **Title-style capitalization**; drop articles ("View Settings", not "View the Settings").
- Dim unavailable items; keep a menu openable even if all items are unavailable.
- Append an ellipsis (…) when more input is needed before the action completes.

**Icons**
- Standard icons for standard actions. Use icons sparingly and purposefully (key actions, locations, devices, visual concepts like rotate, user content). No icon if none clearly fits.
- Within a group: icons on all items or none.

**Organization**
- Most important/frequent items first. Group related items with separators; keep related commands together even if used less (Paste and Match Style with Paste).
- Watch menu length — split into menus or use a submenu. User-generated/dynamic menus (history, bookmarks) may be long and scroll.

**Submenus**
- Sparingly — e.g. when a term repeats in more than two items ("Sort by" → Date, Score, Time); use the repeated term as the label. Indicated by a chevron.
- One level deep; if a submenu exceeds about **five items**, consider a separate menu.
- Keep the submenu item openable even if its children are unavailable. Prefer submenus to indentation.

**Toggled items**
- One item with a changing label (Show Map ↔ Hide Map); add verbs if ambiguous ("Turn HDR On").
- Or show both items when seeing both states helps.
- Checkmarks for attributes in effect; offer a "Plain"-style item to clear many attributes.

**In-game menus:** navigate with the platform's standard input (touch on iOS/iPadOS); keep text and targets large enough when scaling to small screens.

**iOS/iPadOS menu layouts (`preferredElementSize`)**
- Small: top row of **4** icon-only items, then a list. Only for closely related actions (Bold, Italic, Underline, Strikethrough) with recognizable symbols.
- Medium: top row of **3** items with icon and short label, then a list. For three common key actions (Notes: Scan, Lock, Pin).
- Large (default): everything as a list.

## Ornaments
Source: https://developer.apple.com/design/human-interface-guidelines/ornaments

**Not supported on iOS or iPadOS** (visionOS floating controls attached to windows).

## Pop-up buttons
Source: https://developer.apple.com/design/human-interface-guidelines/pop-up-buttons

- A flat list of **mutually exclusive options/states**; the button shows the current choice. For actions, multi-select or submenus, use a pull-down button.
- Provide a sensible default most people want.
- Make options predictable without opening (introductory label or descriptive button label).
- Good when space is tight. A "Custom" option can hold rarely needed choices; explanatory text below the list is fine.
- **iPadOS:** in a popover or modal, a pop-up button can replace a disclosure indicator for a small, well-defined set of options on a list row.

## Pull-down buttons
Source: https://developer.apple.com/design/human-interface-guidelines/pull-down-buttons

- A menu of actions/items directly related to the button (Add → what to add; Sort → by which attribute; Back → which earlier location). Non-command choices → pop-up button.
- Don't hide all of a view's primary actions inside one pull-down.
- Aim for **at least three items** (one or two → use buttons/toggles); not so many that scanning is slow.
- Menu title only if it adds meaning.
- Destructive items shown in red and confirmed via an action sheet (iOS) or popover (iPadOS).
- Icons after labels only when they clarify (SF Symbols).
- **iOS/iPadOS:** pull-down menus can also open on a gesture (touch and hold Safari's Tabs button). A **More** (ellipsis) pull-down saves space but hurts discoverability — balance carefully.

## The menu bar
Source: https://developer.apple.com/design/human-interface-guidelines/the-menu-bar

**iPadOS only** on mobile (not iOS). Hidden until people move the pointer to the top edge or swipe down; centered; occupies the status bar area; no Apple menu or menu bar extras; window controls appear in it when the app is full screen; app menu lacks About/Services/visibility items.

- Standard order: **AppName, File, Edit, Format, View, app-specific menus, Window, Help**. Support system menus and their order; standard items often work automatically.
- Always show the same items; disable (don't hide) unavailable ones.
- Standard icons; support standard keyboard shortcuts (same patterns as macOS); custom shortcuts only when needed.
- Short, one-word menu titles (title case if more).
- **App menu:** Settings… opens your page in iPadOS Settings; link your in-app preferences with a separate item beneath it in the same group, along with other app-wide configuration.
- **File menu:** New *Item* (name the type), Open…, Open Recent (names not paths, most recent first, Clear Menu), Close / Close Tab / Close File, Save (auto-save anyway), Duplicate (prefer to Save As/Export/Copy To), Rename…, Move To…, Export As… (only for formats you don't normally handle), Revert To, Page Setup…, Print…. Rename or drop File if the app has no files.
- **Edit menu:** Undo/Redo with specific targets ("Undo Typing"), Cut, Copy, Paste, Paste and Match Style, Delete (not Erase/Clear), Select All, Find submenu, Spelling and Grammar, Substitutions, Transformations, Speech; system adds Start Dictation and Emoji & Symbols. Put Find in File if it searches objects rather than content.
- **Format menu:** Font and Text submenus; omit if no rich-text editing.
- **View menu:** show/hide items reflect current state (Show/Hide Tab Bar, Toolbar, Sidebar), Customize Toolbar, Enter/Exit Full Screen. Provide View even if minimal. iPadOS: consider listing each tab as a View menu item with key bindings.
- **App-specific menus** between View and Window: list all custom commands (findability, shortcuts, Full Keyboard Access); mirror the app's hierarchy (Mailbox → Message → Format); order most general to most specific.
- **Window menu:** Minimize, Zoom (not for full screen), tab navigation, Merge All Windows, Bring All to Front, open windows alphabetically (no panels).
- **Help menu:** app help, feedback, few extras behind a separator.
- **Dynamic (modifier-key) items:** never the only way to do something; menu bar only; a single modifier key.
- iPadOS specifics: the bar is often hidden in full screen, so **every function must be reachable in the app UI**, especially dynamic items (hardware keyboard only). Don't use the menu bar as a catch-all. Use submenus more often than on Mac (rows are taller).

## Toolbars
Source: https://developer.apple.com/design/human-interface-guidelines/toolbars

Controls along the top or bottom edge: the view title, navigation (back/forward, search) and actions. (Tab bars are for switching app sections.) In iOS a top toolbar is often called a navigation bar.

**Best practices**
- Don't overcrowd. Decide which items move to overflow at narrow widths; iPadOS adds an overflow menu automatically — don't add one yourself or design layouts that overflow by default.
- Use a **More** menu only if really needed, for lower-priority actions.
- iPadOS: consider letting people customize the toolbar (apps with many items or long sessions).
- **Avoid custom toolbar backgrounds and tinted controls** — let content inform the look; use a scroll edge effect (`ScrollEdgeEffectStyle`) to separate the bar. Don't color item labels like a colorful content background.
- Use standard components (their corner radii are concentric with the bar); custom ones must match that concentricity.
- Optionally hide toolbars for distraction-free viewing, with a reliable way to restore them.

**Titles**
- Give each view a useful title (may be empty if content already makes it obvious). **Never your app's name.** Keep it **under 15 characters**.
- **iOS:** use a **large title** that collapses to a standard title on scroll and returns at the top (`prefersLargeTitles`).

**Navigation**
- Use the standard Back and Close buttons with the standard symbols — **don't use text labels "Back" or "Close"**. Custom versions must look and behave the same, consistently.

**Actions**
- Prioritize the most likely/important commands. Every item's meaning must be obvious.
- Prefer simple symbols over text (except things like Edit). Use system symbols **without borders** (no outlined circles) — the section is already a container.
- Key action (Done, Submit) uses the `.prominent` style — **only one**, on the **trailing** side.

**Groupings** (leading · center · trailing)
- Leading: back, sidebar toggle, title, optional document menu (Duplicate, Rename, Move, Export) — not customizable.
- Center: common controls (customizable and collapsible on iPadOS).
- Trailing: always-visible important items, inspector buttons, optional search, More menu, primary action.
- Group by function and frequency; give navigation and critical actions (Done, Close, Save) their own familiar groups; keep placements consistent across platforms; **at most about three groups**.
- Separate text-labeled buttons from each other and from symbol buttons with fixed space so they don't read as one.
- **iOS:** only the essentials in the main bar; the rest in More.
- **iPadOS:** a toolbar and a tab bar can share the top row.

---
# Navigation and search
Overview: https://developer.apple.com/design/human-interface-guidelines/navigation-and-search

## Path controls
Source: https://developer.apple.com/design/human-interface-guidelines/path-controls

**Not supported on iOS or iPadOS** (macOS).

## Search fields
Source: https://developer.apple.com/design/human-interface-guidelines/search-fields

- Placeholder text tells people what they can search. Search as people type. Show recent searches and predictive suggestions. Most relevant results first; consider categories. Allow filtering results.
- **Scope bar:** filter among clearly defined categories (Mail: all mailboxes vs. current); default to the broader scope.
- **Tokens:** encapsulated, editable search terms that filter (a contact in Mail, "photos" in Messages); pair with suggestions so people discover them.

**iOS — three entry points**
- **Search tab** in the tab bar (trailing end). *Standard tab* style → a landing page with suggestions/categories for exploration (TV app). *Button appearance* → jumps straight to a focused field with the keyboard and returns to the previous tab afterward, for quick lookups.
- **Toolbar:** prefer the **bottom** (field or button that animates above the keyboard) when search is a priority (Settings, Mail, Notes). Use the **top** (navigation bar button) when bottom content must stay unobstructed or there's no bottom toolbar (Wallet).
- **Inline field** next to the content it filters (Music library); place it above the list and consider pinning it to the top toolbar on scroll.

**iPadOS**
- Trailing side of the toolbar is the common spot, especially with split views (Mail, Notes) or when results show in the detail view.
- Top of the sidebar to filter sidebar navigation (Settings).
- A dedicated sidebar/tab item for discovery-heavy search (Music, TV); focus the field on arrival — **except** when only the virtual keyboard is available (don't let it cover the view unexpectedly).
- Keep search contextually available when the window shrinks to compact (Notes/Mail put it above the list column). Keep iPad and Mac experiences consistent.

## Sidebars
Source: https://developer.apple.com/design/human-interface-guidelines/sidebars

- Leading-side navigation between app areas or top-level collections; needs lots of space — a tab bar (or a tab bar that converts to a sidebar) is often better.
- Sidebars float in the Liquid Glass layer; extend rich content beneath them (horizontal scrolling or `backgroundExtensionEffect()`).
- Let people customize contents and order when possible.
- Use disclosure controls to group a large hierarchy; **no more than two levels** — deeper → split view with a content list column. Title groups with short labels.
- Use SF Symbols (or custom symbols, not bitmaps) for items.
- Let people hide it with familiar interactions (edge swipe on iPad), but **don't hide it by default**.
- Icons use the app accent color by default; fixed colors only where they carry meaning (Mail's yellow VIP).
- **iOS/iPadOS:** the `sidebarAdaptable` tab view can open as sidebar or tab bar with a toggle and adapts to rotation and resizing. Sidebar-only: `NavigationSplitView` / `UISplitViewController`. **Consider a tab bar first.** UIKit lists: use the `.sidebar` list appearance.

## Tab bars
Source: https://developer.apple.com/design/human-interface-guidelines/tab-bars

- For **navigation between top-level sections only — not actions** (use a toolbar for actions). Preserves each section's navigation state.
- Keep it visible in every section (only modals may cover it).
- Use as few tabs as the hierarchy needs; complex apps → sidebar or sidebar-adaptable tab bar.
- **Avoid overflow**: when space runs out, the trailing tab becomes "More", which hides content.
- **Never disable or hide tabs**, even when empty — explain why the section is empty.
- Label every tab, ideally one word.
- Use SF Symbols, **prefer filled** variants. Icons sit above labels in compact width, beside them in regular width. Custom icon sizes: Apple Design Resources.
- Badges (red oval, white number or "!") only for critical info.
- Colorful content → monochrome tab bar or a clearly different accent.
- **iOS:** floats on Liquid Glass at the bottom. With an accessory (e.g. MiniPlayer), it can minimize on scroll with the accessory inline; tap a tab or scroll to top to restore (`TabBarMinimizeBehavior`). Optional dedicated search tab at the trailing end.
- **iPadOS:** appears near the top; fixed (`tabBarOnly`) or convertible to a sidebar (`sidebarAdaptable`). Prefer the tab bar for main sections. Allow customization (add favorites, remove rarely used) but keep the default at **five or fewer** tabs for continuity between compact and regular sizes.

## Token fields
Source: https://developer.apple.com/design/human-interface-guidelines/token-fields

**Not supported on iOS or iPadOS** as a component (macOS). For search tokens on iOS/iPadOS see Search fields.

---
# Presentation
Overview: https://developer.apple.com/design/human-interface-guidelines/presentation

## Action sheets
Source: https://developer.apple.com/design/human-interface-guidelines/action-sheets

SwiftUI: `confirmationDialog`; UIKit: `UIAlertController` with `.actionSheet`.
- Use an action sheet — **not an alert** — for choices tied to an action the person deliberately took (cancelling a Mail draft → Delete Draft / Save Draft).
- Use sparingly.
- One-line title; message only if necessary.
- Include **Cancel** at the bottom when an action could destroy data (SwiftUI adds it by default).
- Destructive buttons use the destructive style and go at the **top**.
- **iOS/iPadOS:** action sheet, not a menu, for choices that follow an action. Never let it scroll — keep the button count low.

## Alerts
Source: https://developer.apple.com/design/human-interface-guidelines/alerts

- Use sparingly — only essential info with useful actions.
- Not for purely informational messages (use inline indicators, like Mail's connection status).
- No alerts for common, undoable actions even if destructive (deleting an email). Do alert for **uncommon, irreversible** destructive actions.
- **No alerts at launch** — show cached/placeholder data and a quiet inline label for problems like no network.

**Content:** title, optional message, **up to three buttons**; iOS/iPadOS alerts may include a text field (only when input is required, e.g. a secure password field).
- Direct, neutral, non-accusatory tone; don't hide severity.
- Title: what happened, in what context, and why — never "Error" or a bare code; no more than **two lines**. Full sentence → sentence case with punctuation; fragment → title case, no punctuation.
- Message only if it adds value: short, complete sentences.
- Don't explain the buttons; if you must, say "choose" and use the exact button title without quotes.

**Buttons**
- One or two words describing the result; verbs tied to the text ("View All", "Reply", "Ignore"). Sentence case, no punctuation.
- "OK" only in purely informational alerts; avoid "Yes"/"No". Use specific verbs ("Erase", "Delete", "Convert").
- Always title the cancel button **"Cancel"**; never make Cancel the default. Single-button default alert → "Done", not "Cancel". To force reading, make no button the default.
- Most likely/default button on the **trailing** side of a row or **top** of a stack; Cancel on the leading side or bottom.
- Destructive style only for destructive results the person **didn't deliberately choose** (not on "Empty Trash" after they chose Empty Trash).
- Any destructive action → include Cancel.
- Alternative dismissals: going to the Home Screen; Esc or Command-Period on a keyboard.
- **iOS/iPadOS:** choices related to a deliberate action → action sheet instead. Avoid alerts that scroll (short title, brief message) — test at large text sizes.

## Page controls
Source: https://developer.apple.com/design/human-interface-guidelines/page-controls

- Dots for an ordered, flat sequence of pages only (not hierarchical — use sidebar/split view for that). Center horizontally near the bottom.
- **More than about 10 dots** is hard to read — use a grid or other layout.
- Custom indicators: simple images (no negative space, text or inner lines; SF Symbols work), only when they add meaning (Weather's `location.fill` for current location; `bookmark.fill` as default for bookmark pages). **No more than two indicator image types.** Don't color indicators — let the system.
- **iOS/iPadOS:** current dot highlighted; edge dots shrink when there are too many. Tap leading/trailing side for previous/next; scrub to move quickly (past an edge jumps to first/last); iPad pointer can target a dot. **Don't animate page transitions while scrubbing** — only on tap.
- Background styles: *automatic* (only while interacting — when not primary navigation), *prominent* (always — only when it's the screen's primary navigation), *minimal* (never — position only; **don't enable scrubbing** with minimal).

## Panels
Source: https://developer.apple.com/design/human-interface-guidelines/panels

**Not supported on iOS or iPadOS** (macOS floating panels/HUDs). On iOS/iPadOS use a modal view, sheet, popover or split-view inspector pane.

## Popovers
Source: https://developer.apple.com/design/human-interface-guidelines/popovers

- Small amount of info or a few related tasks (calendar event edits); good for temporary content instead of a permanent sidebar.
- Arrow points directly at the source; don't cover the source or essential content.
- Close/Cancel/Done only when it clarifies (e.g. save vs. discard); otherwise tapping outside or choosing an item closes it. Multi-select popovers stay open until dismissed.
- Auto-dismissed nonmodal popovers must **save work**; discard only on explicit Cancel.
- **One popover at a time** — never cascades. Nothing on top of a popover except an alert.
- Let one tap close the current popover and open another (adjacent bar buttons).
- Size to content; animate size changes.
- Don't say "popover" in help text. **Never use a popover for warnings** — use an alert.
- **iOS/iPadOS:** **no popovers in compact width** — use a sheet/full-screen modal instead.

## Scroll views
Source: https://developer.apple.com/design/human-interface-guidelines/scroll-views

- Support standard scrolling gestures and keyboard shortcuts; custom scrolling must keep elastic (rubber-band) indicators.
- Signal scrollability — e.g. show partial content at the edge.
- **Never nest scroll views of the same orientation** (horizontal inside vertical is fine).
- Page-by-page scrolling where it fits, optionally with a small overlap for context (`PagingScrollTargetBehavior`).
- Auto-scroll only as much as needed: to bring search hits/insertion point into view, when typing resumes elsewhere, when a drag-selection passes the edge, before acting on an off-screen selection.
- Set sensible min/max zoom.

**Scroll edge effects** (separate floating bars from scrolling content)
- Prefer the **automatic** style (more opaque for busy top toolbars, text outside glass controls, pinned headers). Test thoroughly if you choose *soft*; *hard* is also available.
- Use only behind floating UI — it's not decoration or a dimming overlay.
- One per view; in iPad split views each pane may have one — keep heights consistent.
- **iOS/iPadOS:** pair paging scroll views with a page control, and then hide the scroll indicator on that axis.

## Sheets
Source: https://developer.apple.com/design/human-interface-guidelines/sheets

- For a scoped task related to the current context (attach a file, choose a location). On iOS/iPadOS sheets may be **modal or nonmodal** (Notes' formatting sheet edits the note while open).
- Buttons: **Cancel/Close** dismisses without saving; **Done** completes/saves; **Back** goes to a previous step (doesn't dismiss).
- Complex or long flows → full-screen modal instead (`.fullScreen`) — media, camera, multistep editing.
- **One sheet at a time** from the main UI; close the first before presenting another (re-show later if needed).
- Nonmodal sheet for supplementary tools affecting the parent view.
- A Done button must always be paired with Cancel (or Back in a flow). **Never show Cancel, Done and Back together.**
- **iOS/iPadOS placement:** single-view sheets → **Cancel on the leading edge** of the top toolbar, **Done on the trailing edge**. Multi-step flows vary by step (e.g. Cancel + Next first, Back + Next middle, Back + Done last).
- **Detents:** *large* (full height, always supported) and *medium* (about half); custom detents possible. iPhone: add medium for progressive disclosure (share sheet); full-height only when creation needs space (Mail/Messages compose).
- Show a **grabber** on resizable sheets (drag to resize, tap to cycle detents; works with VoiceOver).
- Support **swipe down to dismiss**; with unsaved changes, confirm via an action sheet.
- **iPadOS:** prefer **page** or **form sheet** presentation styles.

## Windows
Source: https://developer.apple.com/design/human-interface-guidelines/windows

**iPadOS only** (iOS has no windows). Primary windows hold main navigation; auxiliary windows hold one task and a close button.
- Adapt fluidly to every size.
- Open new windows deliberately (Mail compose) — not by default; offer "Open in New Window" via context menu or File menu (`OpenWindowAction`).
- **No custom window frames or controls**; don't imitate system chrome.
- Call them "windows" in UI copy (never "scenes").
- **iPadOS modes:** full screen (switch via app switcher) or windowed (free resize, overlap, remembered size/position).
- Windowed mode puts window controls at the **leading edge of the toolbar** — move leading toolbar buttons inward when they appear so they aren't covered.
- Consider a gesture to open content in a new window (pinch to expand a note). You must support multiple windows even if you show a single file via Quick Look scene activation.

---
# Selection and input
Overview: https://developer.apple.com/design/human-interface-guidelines/selection-and-input

## Color wells
Source: https://developer.apple.com/design/human-interface-guidelines/color-wells

- A color well opens a color picker. Prefer the system picker — familiar, consistent across iOS/iPadOS/macOS, and lets people save colors across apps (SwiftUI `ColorPicker`).

## Combo boxes
Source: https://developer.apple.com/design/human-interface-guidelines/combo-boxes

**Not supported on iOS or iPadOS** (macOS).

## Digit entry views
Source: https://developer.apple.com/design/human-interface-guidelines/digit-entry-views

**Not supported on iOS or iPadOS** (tvOS).

## Image wells
Source: https://developer.apple.com/design/human-interface-guidelines/image-wells

**Not supported on iOS or iPadOS** (macOS).

## Pickers
Source: https://developer.apple.com/design/human-interface-guidelines/pickers

- Scrollable lists of distinct values (single or multipart). Values and order follow the device language/region.
- Best for **medium-to-long** lists. Short lists → pull-down button; very large sets → list/table (with index).
- Values must be predictable and logically ordered (e.g. alphabetical countries).
- Show the picker in context (near the edited field, at the bottom of the window or in a popover) — don't switch views.
- Minute granularity can be coarser if it divides 60 evenly (e.g. 0, 15, 30, 45).
- **iOS/iPadOS date picker styles:** *compact* (button showing the value in the accent color; opens a modal editor — use when space is tight), *inline* (wheels for time only; calendar for date/time), *wheels* (scrolling wheels, also keyboard entry), *automatic*.
- **Modes:** date; time (optional AM/PM); date and time; countdown timer (up to 23 h 59 min; not in inline or compact styles).

## Segmented controls
Source: https://developer.apple.com/design/human-interface-guidelines/segmented-controls

- Two or more equal-width segments acting as buttons; on iOS/iPadOS a single choice from a set (or momentary actions).
- For closely related choices affecting an object, state or view; keeps grouping and shows selection clearly.
- Don't mix selection segments with action segments in one control.
- **No more than about 5 segments on iPhone** (about 5–7 on wide layouts).
- Keep segment widths and content sizes consistent.
- Use text **or** images in one control — not both.
- Labels: nouns/noun phrases, title case; no introductory text needed.
- **iOS/iPadOS:** good for switching between closely related subviews (Calendar's New Event vs. Reminder). For separate app sections, use a tab bar.

## Sliders
Source: https://developer.apple.com/design/human-interface-guidelines/sliders

- A thumb on a track between min and max; the filled track shows the value; optional min/max icons (small image ↔ large image).
- Customize track color, thumb and icons only when it adds meaning.
- Minimum on the **leading** side, maximum on the **trailing** side (vertical: min at bottom).
- For wide ranges, pair with a text field (exact value) and a stepper (whole increments).
- **iOS/iPadOS:** **never use a slider for audio volume** — use the system volume view (`MPVolumeView`).

## Steppers
Source: https://developer.apple.com/design/human-interface-guidelines/steppers

- Two-segment +/− control placed next to a field showing the value (the stepper itself shows nothing) — make the affected value obvious.
- For potentially large changes, pair with a text field (e.g. number of copies).

## Text fields
Source: https://developer.apple.com/design/human-interface-guidelines/text-fields

- For small, specific input (name, email). Longer text → text view.
- Placeholder hint ("Email", "Password"); since it disappears on typing, also consider a persistent label.
- **Secure text field** for passwords and sensitive data (`SecureField`).
- Size fields to the expected amount of text. Space multiple fields evenly; stack vertically with consistent widths per kind.
- Logical tab/focus order (usually automatic).
- Validate at the right time: email on leaving the field; user name/password before leaving the field. Digit-only fields must flag non-digits.
- Use number formatters for numeric data; don't assume a presentation — formatting varies by locale.
- Choose clipping, wrapping (character/word) or truncation (start/middle/end) deliberately.
- **iOS/iPadOS:** show the matching keyboard type. Put a **Clear button** at the trailing end. Leading-end image = field's purpose; trailing-end button = extra feature (e.g. Bookmarks).

## Toggles
Source: https://developer.apple.com/design/human-interface-guidelines/toggles

- For two opposing states (on/off) of content or a view; other choices → e.g. pop-up button.
- Make clear what it affects; make the states visually obvious (fill, background, checkmark) — **not color alone**.
- **iOS/iPadOS:** use the **switch** style **only in list rows** (the row text is the label — no extra label needed). Default green is fine; change to the accent color only if needed and with enough contrast versus the off state.
- Outside lists, use a **button that behaves like a toggle** (icon + changing background, like Phone's filter button) — no explanatory label (`changesSelectionAsPrimaryAction`).

## Virtual keyboards
Source: https://developer.apple.com/design/human-interface-guidelines/virtual-keyboards

- Match the keyboard to content and set the semantic content type so the system can tailor keys and suggestions (`keyboardType`, `textContentType`). Types: ASCII capable, ASCII number pad, decimal pad, default, email address, name/phone pad, number pad, numbers and punctuation, phone pad, Twitter, URL, web search.
- Customize the Return key when it clarifies the action (e.g. Search) — `submitLabel`.
- **Custom input views** (replace the keyboard inside your app, like Numbers' numeric pad): must be clearly beneficial in context; play the standard click (`playInputClick()`).
- **Custom keyboard extensions** (system-wide; not used in secure or phone-number fields): only for genuinely unique input or unsupported languages; provide an obvious keyboard switch (like the Globe key); don't duplicate the system Emoji/Globe or Dictation keys; teach usage inside your app, not inside the keyboard.
- **iOS/iPadOS:** use the keyboard layout guide so the keyboard feels integrated and important UI stays visible (`UIKeyboardLayoutGuide`). Controls above the keyboard (input accessory view) must be task-relevant; use a standard toolbar (gets Liquid Glass automatically) or apply Liquid Glass to match; use standard padding.

---
# Status
Overview: https://developer.apple.com/design/human-interface-guidelines/status

## Activity rings
Source: https://developer.apple.com/design/human-interface-guidelines/activity-rings

- Use when relevant (health/fitness apps, especially those writing to HealthKit) — e.g. on a workout metrics or summary screen.
- **Only** for Move, Exercise and Stand; never for other data, and never show those metrics in another ring-like element.
- One person's progress only, with a clear label/photo/avatar showing whose.
- Never alter appearance: don't change colors, opacity or apply filters; **always on a black background**; prefer enclosing rings + background in a circle by adjusting the container's corner radius (not a mask); keep black visible around the outer ring (thin black stroke if needed; no gradients/shadows/effects); scale appropriately; adapt the surroundings to the rings, not vice versa.
- Ring-related labels/values use the matching ring colors (RGB values on the source page).
- Outer margin at least the gap between rings; nothing may crop or encroach.
- Separate any other rings with padding, lines, labels, color and scale.
- Don't duplicate Activity app notifications; never put rings in notifications. Not for decoration, labels, backgrounds, branding, app icons or marketing.
- **iOS:** `HKActivityRingView`; shows all three rings when an Apple Watch is paired, otherwise just Move (history can mix both).

## Gauges
Source: https://developer.apple.com/design/human-interface-guidelines/gauges

- Show a value within a range on a circular or linear path; standard style (indicator) or capacity style (fill). An *accessory* variant matches complication styling — good for iOS Lock Screen widgets.
- Write short labels for the value and both endpoints (VoiceOver reads them).
- A gradient fill can reinforce meaning (red→blue for hot→cold).

## Progress indicators
Source: https://developer.apple.com/design/human-interface-guidelines/progress-indicators

Determinate (bars fill leading→trailing; circles fill clockwise) vs. indeterminate (spinning activity indicator). `ProgressView`.
- Prefer **determinate** whenever possible.
- Report progress accurately and evenly (don't hit 90% in 5 seconds and sit on the last 10% for 5 minutes).
- Keep it moving; a frozen indicator looks like a hang — if a process stalls, explain what's wrong and what to do.
- Switch indeterminate → determinate once duration is known.
- **Never switch between spinner and bar** styles.
- Optional short description with real context — avoid vague words like "Loading" or "Authenticating".
- Consistent placement.
- Offer Cancel when safe; add Pause if cancelling loses work; confirm cancellations that lose progress (alert with resume option).
- **iOS/iPadOS refresh control** (pull to refresh, `UIRefreshControl`): still refresh automatically on a schedule — never make people pull for every update. Title only if useful (e.g. last update time), never instructions on how to pull.

## Rating indicators
Source: https://developer.apple.com/design/human-interface-guidelines/rating-indicators

**Not supported on iOS or iPadOS** as a system component (macOS). If you build star ratings: allow inline rank changes and keep the symbol recognizable (stars).

---
# System experiences
Overview: https://developer.apple.com/design/human-interface-guidelines/system-experiences

## App Shortcuts
Source: https://developer.apple.com/design/human-interface-guidelines/app-shortcuts

Built with App Intents; available right after install via Siri, Spotlight, the Shortcuts app, the Action button and Apple Pencil squeeze. **Up to 10 App Shortcuts per app.** People can also compose their own shortcuts from your actions.

- For common domains, adopt **App schemas** (Apple Intelligence / Siri) first; use App Shortcuts for unique features or content outside those schemas.
- Offer shortcuts for the most common, important tasks — ideally completed without leaving the current context (open the app only when it helps multistep tasks).
- At most one optional parameter with predictable values ("Start [morning, daily, sleep] meditation"). If missing, ask — suggest a likely default (most recent, time of day) plus a short list.
- Keep phrases simple to say; ask for extra info in a follow-up step.
- Promote them in-app with occasional tips (`SiriTipUIView`).
- Responses: spoken dialogue, **snippets** (static info or confirmations), **Live Activities** (ongoing changing info like timers). Put all critical info in the full dialogue for audio-only devices (AirPods, HomePod).
- **Phrases:** brief, memorable, with natural variants; **must include the app name** ("Create a Keynote", "Add a new presentation in Keynote").
- Copy: "App Shortcuts" and "Shortcuts" (the app) in title case, Shortcuts plural; individual "shortcuts" lowercase.
- **iOS/iPadOS:** appear in Spotlight (Top Hit and Shortcuts area) with an SF Symbol or preview image; order them by importance (the system later reorders by usage).

## Complications
Source: https://developer.apple.com/design/human-interface-guidelines/complications

**Not supported on iOS or iPadOS** (watchOS watch faces). Relevant only if the iOS app ships a watchOS companion; see the source page for families and image sizes.

## Controls
Source: https://developer.apple.com/design/human-interface-guidelines/controls

Buttons or toggles in **Control Center, the Lock Screen or the Action button** (iOS/iPadOS 18+). Anatomy: symbol, title, optional value. Control Center shows the symbol (and title/value at larger sizes); the Lock Screen shows the symbol only; the Action button shows symbol + value in the Dynamic Island.

- Offer actions that give the most value without opening the app (e.g. start a Live Activity).
- Update state on interaction, completion or via push; show when an action is in progress.
- The symbol must convey the action alone; toggles need on and off symbols (`door.garage.open` / `door.garage.closed`).
- Animate state changes; animate continuously while a timed action runs.
- Choose a brand-appropriate tint (applies to the on state and Dynamic Island).
- Prompt for required configuration when first added (which light?); allow reconfiguration (`promptsForUserConfiguration()`).
- Action button hint text uses verbs (`controlWidgetActionHint`).
- Variable titles/values need a placeholder for the gallery.
- Redact sensitive titles/values (and optionally state) when locked.
- **Require authentication** for security-affecting actions (unlock doors, start a car) — `IntentAuthenticationPolicy`.
- **Locked camera capture** (iOS 18+, `LockedCameraCapture`): reuse the same camera UI as the app; anything beyond capture requires unlocking; explain how to add the control.

## Live Activities
Source: https://developer.apple.com/design/human-interface-guidelines/live-activities

Track a task/event over a few hours. Starts on iPhone/iPad; appears on the Lock Screen, Home Screen, Dynamic Island and StandBy (iPhone), plus Mac menu bar, Apple Watch Smart Stack and CarPlay Dashboard.

**Required presentations:** *compact* (leading + trailing around the TrueDepth camera, one activity), *minimal* (several activities — up to three in the Dynamic Island, attached/detached circles or ovals), *expanded* (touch and hold), *Lock Screen* (banner at the bottom; also a banner over apps on devices without the Dynamic Island). StandBy uses minimal, then the Lock Screen layout scaled 2×.

**Best practices**
- Only for tasks/events with a defined start and end, **no longer than 8 hours**.
- Show only the glanceable essentials; tap opens the app for detail.
- **No ads or promotions.**
- Avoid sensitive info (visible on Lock Screen/Always-On) — show an innocuous summary or redact, optionally configurable.
- Match your app's look in light and dark. Logo mark without a container — never the whole app icon.
- Don't add app UI that draws attention to the Dynamic Island.
- Large, medium-or-heavier text; small text sparingly.

**Layout**
- Adapt to every device/presentation (see sizes below); use only the space needed.
- **Limited width** (Dynamic Island in landscape): compact/minimal must fit a **28 pt circle** — abbreviations or graphics; if a limited trailing view makes no sense, provide leading only.
- Use Apple Design Resources templates (system margins, text sizes).
- Even, concentric margins; use `ContainerRelativeShape` for rounded elements near corners; separate blocks with inset containers or thick lines; never draw to the Dynamic Island edge.
- Grow/shrink height dynamically as information changes (rideshare: compact while finding a driver, taller with ETA and driver info).

**Color**
- Background color is customizable only on the Lock Screen presentation — ensure contrast, especially in Always-On's reduced luminance. Dynamic Island background is always black — use bold brand colors for text/objects. Tint the key line (shown in dark contexts) to match.

**Animation:** max **2 seconds** per animation (none on Always-On low luminance). Animate updates (numeric content transitions, fades); animate existing elements to new positions on layout changes; avoid overlaps (fade others while one moves).

**Interactivity**
- Tapping opens the app at the right place (deep link).
- Only simple, essential controls (pause/resume playback, workouts, recording) — **ideally one**. Consider letting people respond to updates (contact driver).

**Lifecycle**
- Start at expected moments (order placed, ride requested, match begins); provide an in-app way to stop/unfollow, or people will disable Live Activities entirely.
- Offer an App Shortcut to start it (Action button).
- Update only when content changes. **Alert only for essential updates**; never send push notifications for the same updates.
- Track multiple events in one rotating Live Activity rather than several.
- End immediately when the event ends; it lingers on the Lock Screen up to **4 hours** — set a custom dismissal (usually **15–30 minutes**).

**Per presentation**
- Start with the iPhone design, then refine for StandBy, CarPlay, Apple Watch.
- Compact: the most important dynamic info (two team logos + score); leading and trailing read as one unit (shared color/type); narrow and snug to the camera, no padding, balanced widths (shorter units); both sides link to the same screen.
- Minimal: show live data (Timer shows remaining time), still recognizable.
- Expanded: keep relative positions from compact; wrap tightly around the camera.
- Lock Screen: don't mimic notification layouts; restrained colors for personalized Lock Screens; verify Dark Mode and Always-On; check the auto-generated dismiss button color (`activitySystemActionForegroundColor`); standard margin **14 pt**.
- StandBy: assets must hold up at 2×; consider a custom layout; prefer the default background; keep standard margins; check Night Mode (red tint).
- CarPlay: compact elements combine into one layout; interactive elements are disabled — favor timely content; consider the `small` supplemental family for a custom layout. Sizes 240×78, 240×100, 170×78 pt.

**iOS sizes (pt)**
| Screen (portrait) | Compact (each side) | Minimal | Expanded | Lock Screen | Limited width |
|---|---|---|---|---|---|
| 430×932 | 62.33×36.67 | 36.67–45×36.67 | 408×84–160 | 408×84–160 | 28×28 |
| 393×852 | 52.33×36.67 | 36.67–45×36.67 | 371×84–160 | 371×84–160 | 28×28 |

**iPadOS Lock Screen sizes:** 1366×1024 → 500×84–160; 1194×834, 1012×834, 1080×810, 1024×768 → 425×84–160.

## Notifications
Source: https://developer.apple.com/design/human-interface-guidelines/notifications

Consent required. Styles: banners, badges, Notification Center items. Communication notifications show contact images and group names instead of the app icon.

**Best practices**
- Concise and informative.
- **Never send multiple notifications for the same thing.**
- Don't tell people to go do tasks in the app — offer notification actions for quick tasks instead.
- **Errors belong in alerts, not notifications.**
- In the foreground, surface the info quietly (badge, insert data) instead of a notification.
- No sensitive, personal or confidential info.

**Content**
- Optional short title with real context (headline, event name, subject); title case, no punctuation. If the title would be generic ("New Document"), omit it so the app name shows.
- Body: complete sentences, sentence case, punctuation; don't truncate yourself.
- Provide hidden-preview placeholder text that's generically descriptive ("Friend request", "New comment", "Shipment") — `hiddenPreviewsBodyPlaceholder`.
- Don't include your app name or icon (the system adds them).
- Optional custom sound: short, distinctive, professional; never the only carrier of important info. (Vibration can't be set programmatically.)

**Actions** (up to **four** buttons in the detail view)
- Time-saving actions that avoid opening the app (Calendar's Snooze). Short title-case labels describing the result; no app name.
- **No action that merely opens the app.** Prefer nondestructive actions; give destructive ones enough context (system styles them distinctly).
- Each action gets a simple SF Symbol (shown trailing).

**Badges**
- Only for the count of unread notifications — never weather, dates, prices or scores.
- Never the only way to communicate essential info (people can disable badges).
- Keep them current; setting zero clears related notifications from Notification Center.
- Never draw custom badge look-alikes.

## Snippets
Source: https://developer.apple.com/design/human-interface-guidelines/snippets

Compact views shown after Siri, Spotlight or Shortcuts actions (App Intents). **Confirmation** snippets (Cancel + primary button) are optional; **result** snippets (Done) always appear.
- Anatomy: spoken dialogue (shown above by default), custom view (may include buttons), system buttons.
- Ensure contrast on the system background in light and dark; consistent margins.
- Keep it concise; custom views **no taller than 400 pt** (remember Dynamic Type); deep-link for more detail.
- Primary confirmation label should be specific ("Order", not "OK"/"Proceed"); default is "Continue" (`ConfirmationActionName`).
- Convey purpose visually rather than repeating the dialogue text.

## Status bars
Source: https://developer.apple.com/design/human-interface-guidelines/status-bars

- The status bar is transparent; keep it readable and never imply that content behind it is interactive — prefer a **scroll edge effect** (blur) behind it.
- Hide it temporarily for full-screen media (Photos).
- **Never hide it permanently**; restore with a simple discoverable gesture (single tap).

## Top Shelf
Source: https://developer.apple.com/design/human-interface-guidelines/top-shelf

**Not supported on iOS or iPadOS** (tvOS Home Screen).

## Watch faces
Source: https://developer.apple.com/design/human-interface-guidelines/watch-faces

**Not supported on iOS or iPadOS** (watchOS; iOS apps can offer shareable watch faces for their watch companion — see source).

## Widgets
Source: https://developer.apple.com/design/human-interface-guidelines/widgets

**Sizes and contexts**
- System family: small (iPhone Home Screen, Today View, StandBy, CarPlay, HomeView; iPad also Lock Screen), medium and large (Home Screen, Today View), extra large (**iPad** Home Screen/Today View only).
- Accessory: circular, rectangular, inline on iPhone and iPad **Lock Screen** (corner is watch-only).
- Appearances on Home Screen: light, dark, clear (desaturated + Liquid Glass), tinted (desaturated + user tint). Lock Screen: monochrome/vibrant. StandBy: scaled up, background removed, red tint in low light.
- Rendering modes: **full-color** (Home Screen, Today, StandBy/CarPlay), **accented** (tinted/clear Home Screen — views split into accent and primary groups, both tinted white on iPhone/iPad), **vibrant** (Lock Screen; StandBy night).

**Best practices**
- One simple idea tied to the app's main purpose, with timely content (Weather: current high/low and conditions).
- Give quick access to content and deep links; a widget that just repeats the app icon won't be kept.
- Prefer content that changes through the day; add moments of delight (special occasions).
- Offer multiple sizes only when each adds value — don't just stretch small content. One great size beats all sizes.
- Balance density: essential info at a glance, details on a longer look; too dense → bigger size or graphics.
- Keep to the widget's main purpose at every size (Calendar is always about upcoming events).
- Brand subtly; a small logo in the **top-right corner** only if needed (e.g. multi-source content).
- Decide between auto content (Podcasts) and configurable content (Stocks).
- Don't recreate the widget look inside your app.
- Tell people when signing in adds value ("Sign in to view reservations").

**Updating**
- Widgets refresh periodically, not in real time (system budgets updates). Choose a sensible cadence; show "last updated" text if people may check more often than you can refresh.
- Let the system render live dates/times to save update budget; don't hide stale data behind placeholders.
- Animate updates (max **2 seconds**).

**Interactivity**
- Tap opens the app; buttons and toggles can act without opening it (Reminders checkboxes).
- Simple, directly related actions only; keep it glanceable — no app-like layouts; make targets easy to hit. Inline accessory widgets have a single tap target.
- Deep link to the exact relevant place.

**Margins, text, color**
- Standard margin **16 pt** (tighter **11 pt** for grouped graphics/buttons/backgrounds); Lock Screen and StandBy use smaller margins. Match content corner radii with `ContainerRelativeShape`.
- System font, text styles and SF Symbols; custom fonts sparingly (e.g. big numbers). **Text at least 11 pt.** Never rasterize text. Widgets support Dynamic Type **Large to AX5**.
- Color must not compete with content; never color-only meaning (monochrome/tinted modes).
- Full-color images in tinted/clear modes stand out — reserve for media (album art) and keep them smaller than the widget.
- Full-color mode: light backgrounds in light mode, dark in dark mode; semantic colors.
- Accented mode: deliberately assign accent vs. primary groups (`widgetAccentable`).
- Vibrant mode: full-opacity content; white/light gray for primary, darker grays for secondary; opaque grays rather than white at reduced opacity; check grayscale contrast.

**Gallery**
- Realistic preview (real or realistic simulated data).
- Placeholder while loading: static parts + semi-opaque shapes for dynamic content.
- Description starts with a verb ("See the current weather conditions…"); no "This widget shows…"; sentence case.
- Group all sizes under one description. Optionally color the Add button.

**iOS/iPadOS**
- Lock Screen widgets follow complication principles too: useful info, not just a launcher. Styles: inline above the clock; circular and rectangular below it.
- Support Always-On (reduced luminance — use grays with enough contrast).
- Real-time tracking → Live Activities (build together with widgets).
- **StandBy and CarPlay:** two small widgets side by side, background removed and scaled up — mark the background removable; rely on large text rather than rich images or color.
- Apple HomeView: small widgets on the Modular face (up to four, shared per household) and personal Home Screens.

**iOS widget sizes (pt)**
| Screen (portrait) | Small | Medium | Large | Circular | Rectangular | Inline |
|---|---|---|---|---|---|---|
| 430×932 / 428×926 | 170×170 | 364×170 | 364×382 | 76×76 | 172×76 | 257×26 |
| 414×896 | 169×169 | 360×169 | 360×379 | 76×76 | 160×72 | 248×26 |
| 414×736 | 159×159 | 348×157 | 348×357 | 76×76 | 170×76 | 248×26 |
| 393×852 / 390×844 | 158×158 | 338×158 | 338×354 | 72×72 | 160×72 | 234×26 |
| 375×812 / 360×780 | 155×155 | 329×155 | 329×345 | 72×72 | 157×72 | 225×26 |
| 375×667 | 148×148 | 321×148 | 321×324 | 68×68 | 153×68 | 225×26 |
| 320×568 | 141×141 | 292×141 | 292×311 | — | — | — |

**iPadOS widget sizes (pt, device size; canvas sizes on source page)**
| Screen (portrait) | Small | Medium | Large | Extra large |
|---|---|---|---|---|
| 768×1024, 744×1133 | 120×120 | 260×120 | 260×260 | 540×260 |
| 810×1080 | 124×124 | 272×124 | 272×272 | 568×272 |
| 820×1180, 834×1194 | 136×136 | 300×136 | 300×300 | 628×300 |
| 834×1112 | 132×132 | 288×132 | 288×288 | 600×288 |
| 954×1373, 970×1389 | 162×162 | 350×162 | 350×350 | 726×350 |
| 1024×1366 | 160×160 | 356×160 | 356×356 | 748×356 |
| 1192×1590 | 188×188 | 412×188 | 412×412 | 860×412 |
