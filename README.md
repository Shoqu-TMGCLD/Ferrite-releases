# Ferrite

**A fast, native PowerShell IDE for Windows, in the spirit of the classic PowerShell ISE.**

Ferrite gives you the ISE layout you know (a script pane, a console and command help) on top of Windows PowerShell 5.1, PowerShell 6 and PowerShell 7 and PowerShell Editor Services. It adds IntelliSense, a real debugger, isolated workspaces and module management.

**[⬇ Download the latest version](https://github.com/Shoqu-TMGCLD/Ferrite-releases/releases/latest)** · **[Wiki](wiki/Home.md)** · [All releases](https://github.com/Shoqu-TMGCLD/Ferrite-releases/releases)

## What is Ferrite?

- **Script editor**: syntax highlighting, IntelliSense, signature help, hover, go to definition, rename, folding, find and replace, snippets, PSScriptAnalyzer squiggles and quick fixes.
- **Integrated console**: choose a real terminal (colours, PSReadLine) or the classic ISE output pane with an input line, and switch at any time.
- **Run and debug**: F5 / F8, breakpoints (line, command, variable), step in / over / out, call stack, Variables pane.
- **Every PowerShell**: pick Windows PowerShell 5.1, PowerShell 6 or PowerShell 7 for each PowerShell tab. Local tabs and remote tabs over WinRM or SSH.
- **ISE-style panes**: Commands (with a parameter form), Variables, Outline, Output, Breakpoints, Call Stack.
- **Containers**: colour-coded workspaces, each with its own profile, module path, history and credentials, so client work and sign-ins stay apart.
  - They can be temporary.
  - **Windows Sandbox** mode gives full isolation. A progress window shows the start-up, and **Open desktop** shows the VM.
- **Module management**:
  - inventory of every module and where it loads from
  - updates, install and uninstall
  - conflict detection with **Fix all**
  - module sets per container or project, with lock files
  - signing policies
- **Add-ons**: a `$psIDE` scripting API, and an optional Claude Code pane.
  - The Claude pane can sit on any edge or in its own window.
  - Each container gets its own Claude, and you can choose to share your sign-in.
- **Light, dark or system theme**, ISE keyboard shortcuts, session restore and crash recovery, and a **Welcome** page with what's new and how to use it.
- **In-place updates**: Ferrite checks for new versions and upgrades itself after you confirm.

## Install

1. Download `Ferrite-<version>-x64.msi` from the [latest release](https://github.com/Shoqu-TMGCLD/Ferrite-releases/releases/latest) and run it.
2. Ferrite installs per machine into `Program Files\Ferrite`. It adds a Start menu shortcut and an **Edit with Ferrite** entry for `.ps1`, `.psm1` and `.psd1` files.

**Requirements:** Windows 10 or 11 (x64), plus Windows PowerShell 5.1 (built into Windows) or PowerShell 6 / 7.

Each release has a `.sha256` file next to the installer, so you can check your download:

```powershell
(Get-FileHash .\Ferrite-<version>-x64.msi -Algorithm SHA256).Hash
```

## Updates

**Help > Check for Updates** looks for a new version. The first time one is found, Ferrite asks whether to check automatically once a day.

**Update now** then:
1. downloads the installer and verifies its SHA-256 (and its signature, for signed releases)
2. saves your session and closes Ferrite
3. installs the update (one administrator prompt)
4. reopens Ferrite

## Documentation

The [wiki](wiki/Home.md) covers:
- [Getting started](wiki/Getting-started.md)
- [Features](wiki/Features.md)
- [Containers](wiki/Containers.md)
- [Modules](wiki/Modules.md)
- [Updates](wiki/Updates.md)
- [FAQ](wiki/FAQ.md)

Inside Ferrite, **Help > Welcome to Ferrite** shows what's new in your version and a short guide.

## Feedback and security

- Bugs and ideas: [open an issue](https://github.com/Shoqu-TMGCLD/Ferrite-releases/issues).
- Security problems: please report them privately with **[Report a vulnerability](https://github.com/Shoqu-TMGCLD/Ferrite-releases/security/advisories/new)**, not as a public issue.

## AI assistance

Ferrite is developed with the help of [Claude Code](https://claude.com/claude-code), Anthropic's AI coding assistant. The maintainer directs and tests the work.

## License

Ferrite is released under the MIT license. Third-party components and their licenses are listed in `THIRD-PARTY-NOTICES` in the installation folder.
