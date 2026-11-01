# Designing for iOS and iPadOS

Summarized from Apple's Human Interface Guidelines. Paraphrased; exact specs kept. Open the source link for Apple's exact wording.

## Design principles (all platforms)
Source: https://developer.apple.com/design/human-interface-guidelines/design-principles

Eight principles to weigh trade-offs with:
- **Purpose** — make something meaningful: know what the product is for, focus on the most important features, solve problems in new ways rather than re-creating existing solutions.
- **Agency** — let people do things their way: stay out of the way, let people explore without being locked into flows (guided flows must be skippable), make mistakes easy to recover from.
- **Responsibility** — act in people's best interest: be transparent about what the app does and why (clear rationale for permissions and data), collect only what's needed, anticipate misuse.
- **Familiarity** — build on known concepts, keep visuals and interactions consistent, give clear feedback using system patterns.
- **Flexibility** — design for everyone (accessibility from the start), preserve context across configurations, support many input methods (voice, touch, keyboard…), give each platform the same care.
- **Simplicity** — include just what's necessary (not minimalism), be concise, establish clear hierarchy.
- **Craft** — care about every detail (visuals, animation, wording, audio), prototype and iterate, test in the real world, keep improving after shipping.
- **Delight** — choose the emotion to evoke, create defining moments (even in error messages), but never decoration at the expense of the core task.

## iOS (iPhone)
Source: https://developer.apple.com/design/human-interface-guidelines/designing-for-ios

**Device context**
- Medium-size, high-resolution display. Held in one or both hands, portrait and landscape, viewed at roughly 1–2 feet.
- Input: Multi-Touch gestures, virtual keyboard, voice; apps can also draw on personal data, gyroscope/accelerometer and spatial interactions.
- Sessions range from a minute (check updates, send a message) to an hour+ (browse, games, media). People switch apps often.
- System touchpoints to consider: Widgets, Home Screen quick actions, Spotlight, Shortcuts, activity views (share sheet).

**Best practices**
- Keep onscreen controls few so the primary task and content dominate; make secondary details/actions discoverable within a tap or two.
- Adapt to orientation, Dark Mode and Dynamic Type without breaking; let people choose what suits them.
- Design for how the phone is held: middle and bottom of the screen are easiest to reach. Support swipe-to-go-back and swipe actions on list rows.
- With permission, use platform data instead of making people type it (Apple Pay, Face ID/Touch ID, location).

## iPhone Duo (two-display iPhone)
Source: https://developer.apple.com/design/human-interface-guidelines/designing-for-iphone-duo

Still an iPhone — all iOS guidance applies. Two displays (outer when closed, inner when open), each with a front camera, and a center hinge with many poses (book, flat, standing on an edge). Apps built with standard components and resizable layouts adapt with little work. Test in Xcode Device Hub. (App Store: iPhone Duo screenshots required from April 2027 for apps built with the iOS 27.1 SDK or later — see App Store assets.)

**Layout**
- **Use size classes**, not per-pose layouts: compact width (outer display) and regular width (inner display) cover every pose. Let the existing layout expand — don't reinvent it.
- Use layout margins and safe-area insets; no fixed widths or display-specific dependencies (also supports Split View multitasking sizes).
- Same functionality and element state across displays and poses; you may show an extra hierarchy level on the inner display (Mail: list *or* message closed; both side by side open).
- Games: playable in every pose; may lock orientation but must fill the screen; keep text/control sizes stable; prefer changing aspect ratio over letterboxing (fill any padding with artwork).

**Reserved regions** (areas content avoids): the always-present outer camera (expands into the Dynamic Island for Live Activities), the inner camera (only while active — UI moves aside), and the **folding region** when partially open. System alerts, context menus and sheets move automatically; split views adjust columns to the fold. For custom UI use `ReservedRegion` / `UIView.ReservedRegion`.
- Prefer self-adapting containers (split view panes); use an **even number of grid columns** so content divides at the fold; keep important elements clear of the center.
- Avoid dramatic rearrangement while folding — small adjustments only.

**Split views and arrangement views**
- Split views expand on the inner display and collapse to one pane on the outer display.
- **Arrangement views** (`ArrangementView` / `UIArrangementViewController`) hold a primary and secondary view: *split* (side by side or stacked depending on shape; axes can be limited) or *overlay* (stacked layers that move to either side of the fold when partially folded; secondary can collapse). Use when your layout already resembles HStack/VStack (split) or ZStack (overlay). Keep navigation containers (navigation split views, tab views) **outside** arrangement views.

**Vertical controls**
- On the outer display (and inner display in landscape), toolbars, tab bars, navigation controls, the status bar and the Dynamic Island move to the **side**, preserving vertical space. Inner display in portrait keeps horizontal bars. In Split View each app puts controls on its outer edge. Side controls stay aligned with the hardware (same side even in RTL).
- Account for the asymmetric content area using safe areas (including controls on the opposite edge in Split View).
- Keep controls' relative positions consistent across poses.
- Order: top of the vertical bar = primary navigation (Back, Close), then prominent actions (Done); keep other groups intact.
- Set visibility priorities (`ToolbarItemVisibilityPriority` / `UIBarButtonItemVisibilityPriority`) — items overflow bottom to top by default; keep frequent actions (Compose, New Note) and badged/status items visible longest.
- **Don't override the default side placement.** Full-width layouts are fine where bars aren't needed (Calculator), as long as nothing conflicts with the Dynamic Island/status bar; backgrounds may span full width with inset scrolling content.
- Group items with `ToolbarItemGroup` / `UIBarButtonItemGroup` instead of manual spacing.
- Keep controls next to the content they affect (Mail's list controls stay above the list pane).
- Give every non-text toolbar item **both a title and a symbol** (titles appear in overflow/expanded forms); minimize text-only buttons (they stay in horizontal bars).
- When space runs out: navigation-focused views keep the **tab bar** (toolbar items overflow — default); task-focused views minimize the tab bar to keep toolbar actions (`ToolbarVerticalCompressionBehavior` / `UIVerticalBarCompressionBehavior`).
- Use the system overflow menu (merge your own overflow actions into it); reserve the ellipsis symbol for overflow only.

## iPadOS (iPad)
Source: https://developer.apple.com/design/human-interface-guidelines/designing-for-ipados

**Device context**
- Large, high-resolution display. Held, laid flat, or on a stand; viewing distance up to about 3 feet.
- Input: Multi-Touch, virtual keyboard, hardware keyboard, trackpad/mouse, Apple Pencil, voice — often mixed.
- Quick actions through to hours-long productivity, creation, games and media. Multiple apps onscreen at once; inter-app drag and drop matters.
- System touchpoints: Multitasking, Widgets, Drag and drop.

**Best practices**
- Use the large canvas for content; minimize modal UI and full-screen transitions; put controls within reach but out of the way.
- Choose content size and density based on viewing distance and the active input mode.
- Support touch, hardware keyboard/trackpad and Apple Pencil; consider interactions that combine inputs.
- Adapt to orientation, multitasking window sizes, Dark Mode and Dynamic Type; be ready to run on macOS (iPad apps on Mac).
