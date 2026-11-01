# ios-design-standards

A [Claude Code](https://claude.com/claude-code) plugin and Claude skill.

## ios-design-standards

A skill that keeps Claude aligned with Apple's standards while you design, build or review iPhone and iPad apps. It condenses three Apple sources into iOS- and iPadOS-focused references:

- **Human Interface Guidelines** — Designing for iOS, iPhone Duo and iPadOS, plus every page under Foundations, Patterns, Components, Inputs and Technologies (172 pages)
- **App Store Review Guidelines** — every guideline from 1 to 5 by number, plus the App Review help pages they link to (screenshots, purpose strings, account deletion, kids and age ratings, review prep)
- **App Store asset best practices** — screenshot, app preview and creative asset specs, In-App Events, product page limits, custom product pages, product page optimization, and App Store marketing/trademark rules

Exact specs are kept (tap target sizes, contrast ratios, Dynamic Type tables, widget and Live Activity sizes, screenshot resolutions, character limits), and every section links to its source page.

### What it does

Claude loads the skill automatically when you're working on an iOS or iPadOS app — designing a screen, choosing components, writing UI copy or permission prompts, planning sign-in, privacy or payment flows, or preparing App Store screenshots and metadata. It:

- applies the guidelines while generating SwiftUI/UIKit code or design specs
- reviews existing screens and flows, flagging **Must fix** (App Review rejection risks, accessibility failures) vs. **Should fix** (HIG best practices), each with the rule and a fix
- runs an always-check list of the most common problems before going deeper

You can also invoke it directly: `/ios-design-standards review this onboarding flow`.

### Install

**Claude Code (plugin marketplace — recommended)**

```bash
/plugin marketplace add YusufAq1/ios-design-standards
```

```bash
/plugin install ios-design-standards@ios-design-standards
```

**Claude Code (manual)** — copy the skill folder into your personal skills directory:

```bash
git clone https://github.com/YusufAq1/ios-design-standards.git
```

```bash
cp -r ios-design-standards/plugins/ios-design-standards/skills/ios-design-standards ~/.claude/skills/
```

Or copy it into a project's `.claude/skills/` folder to share it with everyone working on that repo.

**Claude apps (claude.ai / desktop)** — zip the `ios-design-standards` folder (the one containing `SKILL.md`) and upload it under **Settings › Capabilities › Skills**.

### Layout

```
.claude-plugin/marketplace.json          # marketplace listing
plugins/ios-design-standards/
  .claude-plugin/plugin.json             # plugin manifest
  skills/ios-design-standards/
    SKILL.md                             # when to use, workflow, always-check list
    references/
      00-index.md                        # every source page → file and heading
      01-platforms.md                    # design principles, iOS, iPhone Duo, iPadOS
      02-foundations.md
      03-patterns.md
      04-components.md
      05-inputs.md
      06-technologies.md
      07-app-store-review.md
      08-app-store-assets.md
docs/hig-toc-links.md                    # full HIG table of contents
```

### Scope and accuracy

- iOS and iPadOS only. Guidance for watchOS, tvOS, macOS and visionOS was left out; pages that only apply to those platforms are listed with a "Not supported on iOS or iPadOS" note.
- The references are **paraphrased summaries**, not copies of Apple's text. For exact wording, and always before an App Store submission, follow the `Source:` link in each section.
- Content reflects Apple's pages as of November 2026 (App Review Guidelines last updated October 16, 2026). Apple changes these pages regularly — issues and pull requests to keep them current are welcome.

### Disclaimer

This is an unofficial community project. It is not affiliated with, endorsed by, or sponsored by Apple Inc. Apple, iPhone, iPad, App Store, SF Symbols, Liquid Glass and other Apple marks are trademarks of Apple Inc., registered in the U.S. and other countries. The Human Interface Guidelines and App Review Guidelines are © Apple Inc.; this repository contains original summaries that link back to them.

### License

The original summaries, skill instructions and repository structure are released under the [MIT License](LICENSE). This license does not cover Apple's guidelines, trademarks or artwork.
