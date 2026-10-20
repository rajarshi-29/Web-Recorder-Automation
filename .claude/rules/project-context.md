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
|---------|---------|----------|-------------|
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
