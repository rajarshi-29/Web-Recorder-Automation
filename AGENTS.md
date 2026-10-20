# UiPath Project: Web Recorder

Type: Process · Target: Windows · Expressions: VisualBasic · Studio: 26.0.204

## Working here

- Load the `uipath-rpa` skill for anything touching a workflow file. For other `uip` areas use the
  matching skill, or `uip <cmd> --help` — not this file.
- `.xaml`, `.cs` and `project.json` are strict-schema files Studio must be able to reopen. Edit them
  through the skill's conventions, leave the Studio-generated view-state blocks alone, and run
  `uip rpa validate` after every change.
- Done means `uip rpa validate` comes back clean and `uip rpa build` succeeds. A change is not
  finished until both do.
- `uip rpa run` executes on this machine and may drive the desktop UI. Confirm with the user first.
- Only `uip rpa publish` when explicitly asked — it pushes a version to a shared Orchestrator tenant.

## Layout

- `Main.xaml` — entry point
- `project.json` — manifest: dependencies, entry point, expression language, target framework.
  Ground truth; prefer it over the header above, which is a snapshot from creation time.
- `.objects/`, `.screenshots/` — Object Repository source. Commit these.
- `.settings/` — project settings. Commit these.
- `.local/` — generated. Don't edit or commit.

## When something is missing

- **`uip` not found** — ask the user to install it; it needs admin rights and installs runtimes, so
  don't run it yourself. A new shell is needed afterwards before `uip` is on PATH.
  `curl -fsSL https://download.uipath.com/uipath-cli/install.sh | bash` (macOS/Linux) or
  `irm https://download.uipath.com/uipath-cli/install.ps1 | iex` (Windows).
  Install trouble behind a corporate proxy is usually `@uipath` npm scope configuration:
  <https://docs.uipath.com/coding-agents/standalone/latest/user-guide/install-and-set-up>
- **No UiPath skills in your skill list** — run `uip skills install`, then restart the agent session.
  Skills installed mid-session are not loaded into the one already running.
- **Auth error** on anything touching Orchestrator, Studio Web, Integration Service or publishing —
  ask the user to run `uip login`. It opens a browser, so you can't complete it yourself.
  Non-interactive alternative: `uip login --client-id <id> --client-secret <secret>`.
- **No user to ask** (headless or CI) — stop and report the blocker. Don't install, publish, or guess.

<!-- PROJECT-CONTEXT:START -->
<!-- discovery-metadata: cs=0 xaml=1 deps=2 -->
# Web Recorder — Project Context

> Auto-generated project context. Regenerate after significant project changes.

## Overview

| Property | Value |
|----------|-------|
| **Name** | Web Recorder |
| **Type** | Process |
| **Description** | Blank Process |
| **Target Framework** | Windows |
| **Expression Language** | VisualBasic |
| **Studio** | 26.0.204 |

## Dependencies

| Package | Version | Category | Description |
|----------|---------|----------|-------------|
| UiPath.System.Activities | [26.8.2] | Core | Core system activities |
| UiPath.UIAutomation.Activities | [26.10.6] | UI Automation | UI interaction and browser automation |

## Project Structure

```
Web Recorder/
├── Main.xaml                 # Entry-point UI automation workflow
├── project.json              # Process manifest
├── .objects/                 # Object Repository metadata
├── .screenshots/             # Captured UI screenshots
├── .settings/                # Studio settings
└── .local/                   # Generated package/docs/cache data; do not edit
```

| File Type | Count |
|-----------|-------|
| Coded workflows/source (.cs) | 0 |
| RPA workflows (.xaml) | 1 |
| Test cases | 0 |

## Entry Points

| File | Input Arguments | Output Arguments | Purpose |
|------|----------------|------------------|---------|
| Main.xaml | none | none | Opens/attaches to Edge on Google, enters `Open UiPath`, and reads text from the search results page. |

## Conventions

- **Workflow style**: XAML Sequence using modern UI Automation activities (`NApplicationCard`, `NTypeInto`, `NGetText`).
- **Expression language**: Visual Basic.
- **UI targeting**: Captured TargetApp/TargetAnchorable selectors and Object Repository metadata; browser target is Microsoft Edge.
- **Naming observed**: Entry workflow `Main.xaml`; local variable `str_GetText`; display names are descriptive activity names.

## Shared Resources

- **Object Repository**: Edge: Google application metadata exists under `.objects/`; captured screenshots are under `.screenshots/`.

## Architecture

- **Pattern**: Single-workflow process.
- **Execution flow**: Main Sequence → Edge/Google application card → type search text → get result text.
- **External integrations**: Microsoft Edge browser and Google web UI.

## Key Workflow

| Workflow | Purpose | Activities Used |
|----------|---------|------------------|
| Main.xaml | Search Google for `Open UiPath` and capture result text | NApplicationCard, NTypeInto, NGetText |

## Quick Reference

- **Run**: `uip rpa run --file-path "Main.xaml" --project-dir "C:\Users\RajarshiMukherjee\OneDrive - Roboyo Global\Documents\UiPath\Web Recorder" --output json`
- **Validate**: `uip rpa validate --file-path "Main.xaml" --project-dir "C:\Users\RajarshiMukherjee\OneDrive - Roboyo Global\Documents\UiPath\Web Recorder" --output json`
- **Key files to read first**: `Main.xaml`, `project.json`, `AGENTS.md`
<!-- PROJECT-CONTEXT:END -->
