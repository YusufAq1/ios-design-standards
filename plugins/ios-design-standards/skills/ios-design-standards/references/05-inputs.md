# Inputs

Summarized from Apple's Human Interface Guidelines (iOS and iPadOS guidance only). Paraphrased; exact specs kept. Open the source link for Apple's exact wording.
Overview: https://developer.apple.com/design/human-interface-guidelines/inputs

## Action button
Source: https://developer.apple.com/design/human-interface-guidelines/action-button

**iPhone only** (not iPad). People assign an App Shortcut or system function to it in Settings.
- Offer a few essential functions as App Shortcuts ("Start Egg Timer"). Don't offer "open the app" — the system already does.
- Labels (shown in Settings): title case, start with a present-tense verb, no articles/prepositions, **max three words** ("Start Race", not "Started Race" or "Start the Race").
- Don't duplicate the system's own setup tips.
- **iOS:** let actions run without leaving the current context — use Live Activities and snippets (Set Timer asks for a duration and starts a Live Activity without opening Clock).

## Apple Pencil and Scribble
Source: https://developer.apple.com/design/human-interface-guidelines/apple-pencil-and-scribble

**iPadOS only.**
- Support what people do with real pens (e.g. write in margins).
- Controls must respond to Pencil too, so people needn't switch to a finger (Scribble itself is Pencil-only).
- Mark immediately on touch — no mode switch or button first.
- Use tilt (altitude), pressure, orientation (azimuth) and barrel roll to vary strokes; pressure works best for continuous properties (opacity, size).
- Feedback must feel like direct manipulation of the touched content.
- Design for left- and right-handed use; let people move controls a hand might cover.

**Hover:** preview what touching will do (size/color of the mark); don't keep changing the preview with height; **never trigger actions on hover**; preview a mid-range value of dynamic properties; show contextual menus near the tip (e.g. with squeeze or a modifier key); show hover previews for Pencil, not for a pointer.

**Double tap:** respect the user's system setting (switch to eraser / previous tool / show color picker / nothing) where it applies; any custom behavior must be opt-in with a visible mode indicator; never use it to modify content or destroy data — only easily undone actions.

**Squeeze (Pencil Pro):** may be assigned to an App Shortcut by the user; only works while not touching the screen; one quick discrete action (no holds or repeated squeezes); show resulting UI near the Pencil tip; nondestructive and undoable.

**Barrel roll (Pencil Pro):** only to modify marking (e.g. highlighter angle) — never for navigation or showing controls.

**Scribble:** works in all standard text inputs except password fields — custom fields mustn't require a tap first. Make writable anywhere text is natural (Reminders' blank area; `UIIndirectScribbleInteraction`). Hide autocompletion and placeholder text while writing. Keep the field still (delay moves/resizes until a pause). No autoscroll while writing/selecting. Give enough space — enlarge before writing or on pauses, never during.

**Custom drawing (PencilKit):** canvas colors adapt to Dark Mode, but disable that when marking up existing content (PDFs, photos). In compact width the tool picker lacks undo/redo — add them to a toolbar and support three-finger undo/redo.

## Camera Control
Source: https://developer.apple.com/design/human-interface-guidelines/camera-control

**iPhone 16 and later only.** Light press shows an overlay; light double-press lists controls; slide to adjust. Control types: **slider** (range) and **picker** (discrete options); system zoom and exposure controls available.
- Use SF Symbols only (no custom symbols) — Camera & Photos category; symbols don't show state.
- Short control names (Dynamic Type; long names cover the viewfinder).
- Slider values include units/symbols (EV, %) — `localizedValueFormat`.
- Define prominent values the slider snaps to (common or evenly spaced zoom stops) — `prominentValues`.
- Keep your UI out of the overlay area in portrait and landscape; maximize the viewfinder.
- Don't duplicate overlay controls in your UI while the overlay is visible.
- Enable/disable controls by mode (no video controls in photo mode) — the set can't change at runtime.
- Put the most-used controls in the middle; the system remembers the last-used control.
- Provide a locked camera capture extension so the Camera Control can launch your camera from the Lock Screen, Home Screen or other apps.

## Digital Crown
Source: https://developer.apple.com/design/human-interface-guidelines/digital-crown

**Not supported on iOS or iPadOS** (Apple Watch, Apple Vision Pro).

## Eyes
Source: https://developer.apple.com/design/human-interface-guidelines/eyes

**Not supported on iOS or iPadOS** (visionOS gaze targeting).

## Focus and selection
Source: https://developer.apple.com/design/human-interface-guidelines/focus-and-selection

**iPadOS only** (not iOS). Keyboard-driven focus.
- Use system focus effects; custom effects only if absolutely necessary.
- **Never move focus without user interaction** — except when an item focused via directional input disappears (move to a neighbor); otherwise just hide the indicator.
- On iPadOS, support focus for **content** (list items, text fields, search fields) — **not controls** (buttons, sliders, toggles); Full Keyboard Access covers those.
- Platform-consistent focus look: focused list items get white text on an accent-colored highlight; unfocused selection gray.
- Focus ring for text/search fields; full-row highlight for lists and collections.
- **iPadOS focus groups:** Tab moves between groups (sidebar, list, grid); arrow keys move within a group. Halo (focus ring) can be reshaped (rounded corners, Bézier paths) or repositioned if clipped (`UIFocusHaloEffect`). Highlighted appearance (accent-colored text) is automatic for configured collection cells.
- Ensure Tab order follows reading order (leading→trailing, top→bottom); group custom stacks with `focusGroupIdentifier`.
- Raise the priority of the most likely item in a group (`UIFocusGroupPriority`) so it gets focus first.

## Game controls
Source: https://developer.apple.com/design/human-interface-guidelines/game-controls

Always support the platform's default input (touch on iPhone/iPad) as well as controllers.

**Touch controls (iOS/iPadOS, Touch Controller framework)**
- Use virtual controls only when there are many actions or movement; prefer direct interaction with game objects (tap to select).
- Respect safe areas; avoid the Home indicator and Dynamic Island; frequent buttons near the thumbs (outside the movement/camera zones); secondary controls (menus) at the top.
- **Frequent controls at least 44×44 pt; less important (menus) at least 28×28 pt.**
- Visible press state that shows even under a finger (glow), plus sound and haptics.
- Artwork that depicts the action (a sword for attack) — not "A", "X" or "R1".
- Show/hide controls with context (hide movement stick until the player touches).
- Combine actions (double tap, touch and hold for variants; walk/sprint in one control) rather than multi-button combos.
- Movement on the left, camera on the right, with large input areas; dynamic thumbstick where the thumb lands; direct touch panning for camera.

**Physical controllers**
- Provide a fallback to touch on iPhone/iPad; auto-detect paired controllers and their profile.
- Match onscreen labels/glyphs to the connected controller (`GCControllerElement`); with several controllers, match the one in use; prefer SF Symbols for controller buttons over text.
- UI navigation conventions: **A** activates, **B** cancels/back, **shoulders** switch sections left/right, thumbsticks/d-pad move selection, **Menu** opens settings/pauses, **Home** reserved for the system.

**Keyboards (games):** prefer single-key bindings (I = Inventory, M = Map, Space = main action); test comfort on Apple keyboards (Command next to Space vs. Control on others); put related commands on nearby keys (near WASD; number keys for categories); let players remap bindings.

## Gestures
Source: https://developer.apple.com/design/human-interface-guidelines/gestures

- Always provide alternatives (voice, keyboard, Switch Control) — never assume a gesture is possible.
- Keep standard meanings: don't repurpose tap/swipe for app-unique actions, and don't invent gestures for standard actions.
- Respond immediately with feedback that predicts the outcome and shows how far to go.
- Show when a gesture isn't available (locked object, clearly disabled button).
- **Custom gestures** only for frequent specialized tasks (games, drawing) — must be discoverable, easy, distinct, and never the only way to do something important; teach them in context. Shortcut gestures supplement, not replace, standard controls (edge swipe **plus** a Back button).
- Don't conflict with system gestures (defer only in games/immersive cases).

**iOS/iPadOS extra gestures**
| Gesture | Action |
|---|---|
| Three-finger swipe left/right | Undo / redo |
| Three-finger pinch in/out | Copy / paste |
| Four-finger swipe (iPadOS) | Switch apps |
| Shake | Undo / redo |

- Simultaneous gesture recognition is mainly for games (joystick + fire).

**Standard gestures:** tap (activate/select), swipe (reveal actions, dismiss, scroll), drag (move), touch and hold (more controls), double tap (zoom in/out), pinch zoom, rotate.

## Gyroscope and accelerometer
Source: https://developer.apple.com/design/human-interface-guidelines/gyro-and-accelerometer

- Use motion data only for a real benefit (fitness feedback, gameplay); don't collect it for its own sake.
- Motion access requires a purpose string explaining why (shown in the permission request).
- Outside active gameplay, don't use motion to directly manipulate the interface (imprecise, physically hard for some, drains battery).

## Keyboards (hardware)
Source: https://developer.apple.com/design/human-interface-guidelines/keyboards

- Support **Full Keyboard Access** (test it in Settings › Accessibility). On iPadOS don't build custom keyboard navigation for controls (buttons, segmented controls, switches) — FKA handles those; do support focus navigation for text fields, text views, sidebars, collections.
- Respect standard shortcuts; don't repurpose them unless the standard action is meaningless in your app (e.g. no text editing → Command-I could become Get Info).
- Key standards (iPadOS mirrors macOS): Command-N new, O open, S save, Shift-Command-S duplicate/Save As, W close, P print, Q quit, F find, G / Shift-G find next/previous, E use selection for find, A select all, C/X/V copy/cut/paste, Z undo, Shift-Command-Z redo, B/I/U bold/italic/underline, **Command-Comma settings**, Command-Period or Esc cancel, Command-? help, Command-Space Spotlight, Command-Tab app switcher. Full table on the source page.
- **Custom shortcuts** only for the most frequent app-specific commands.
- Modifiers: **Command** primary; **Shift** secondary/complementary; **Option** sparingly for power features; **avoid Control** (system uses it). Avoid extra modifiers on characters not on every keyboard layout.
- List modifiers in the order **Control, Option, Shift, Command**.
- Don't add Shift for the upper character of a key ("Command-?" not "Shift-Command-/").
- Let the system localize and mirror shortcuts for RTL.
- Don't create a shortcut by adding a modifier to an unrelated existing one (no Shift-Command-Z for a non-redo command).
- Expected modifier behaviors: Command-drag moves as a group; Shift-resize keeps aspect ratio; arrow keys nudge by the smallest unit.

## Nearby interactions
Source: https://developer.apple.com/design/human-interface-guidelines/nearby-interactions

Ultra Wideband (Nearby Interaction framework) on supported iPhones; requires permission; uses short-lived random identifiers.
- Ground the interaction in physical-world behavior (bring devices together to hand off audio).
- Use distance, direction and context (share sheet suggests the person you're facing).
- Feedback sharpens with proximity (Find My arrow → pulsing circle); keep it continuous.
- Mix visual, audio and haptic feedback as context shifts (screen vs. environment).
- Never the only way to complete a task.
- Encourage **portrait** orientation implicitly (landscape reduces accuracy); design for the sensor's directional field of view (like the Ultra Wide camera); explain that people/objects in between reduce accuracy.
- **iOS:** provides peer distance and direction.

## Pointing devices
Source: https://developer.apple.com/design/human-interface-guidelines/pointing-devices

**iPadOS** (trackpad/mouse) — adds to touch, never replaces it.
- Respond to standard trackpad gestures consistently; don't redefine system-wide gestures.
- Same experience across touch, pointer and keyboard; modifier-key behaviors (Option-drag to duplicate) identical with touch and pointer.
- Let the pointer reveal auto-hidden controls (minimized toolbars, playback controls).
- Support band (rectangle) multi-select in custom views (`UIBandSelectionInteraction`).
- Distinguish pointer vs. finger only when it adds value (precise seek on a scrubber).

**Pointer shapes and content effects**
- Default arrow; system shapes like the I-beam over text. Content effects: **highlight** (Liquid Glass shape behind controls in a glass container — bar buttons, tab bars, segmented controls, edit menus), **lift** (scale + shadow + specular — standalone glass controls, small opaque elements, app icons), **hover** (custom scale/tint/shadow for large elements).
- Pointer accessories (e.g. resize arrows): simple images; animate accessory transitions to show state changes (`plus` → `circle.slash`).
- Prefer system effects and standard pointers for standard buttons and text areas.
- Hit-region padding: about **12 pt around bezeled elements**, about **24 pt around unbezeled elements**. Make adjacent custom bar-button hit regions contiguous.
- Custom elements that behave like standard ones should use standard effects; be consistent; no gratuitous effects; keep custom shapes simple; useful annotations are fine (X/Y values, dimensions); **no instructional text on the pointer**.
- Scale only elements with room to grow (not table rows); with little space use tint without scale/shadow; never shadow without scale.

## Remotes
Source: https://developer.apple.com/design/human-interface-guidelines/remotes

**Not supported on iOS or iPadOS** (Apple TV Siri Remote).
