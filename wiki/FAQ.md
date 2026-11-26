# FAQ

### Which PowerShell does Ferrite need?

PowerShell 7.4 or later (`pwsh`). Ferrite finds it automatically; to use a specific install, set its path in **Tools > Options**.

### The console says the session failed to start.

Check that `pwsh` runs from a command prompt. Then use **Tools > Restart PowerShell Session** and look in the **Output** pane (View > Show Output) for the error. Remote tabs need WinRM or SSH set up on the target computer.

### Should I use Terminal or Classic console mode?

**Terminal** is a real terminal with colours and PSReadLine, best for interactive work. **Classic** is the ISE's output pane with an input line. Switch any time in **View > Console Mode**.

### Where are my settings?

`%APPDATA%\Ferrite\settings.json` (options) and `%APPDATA%\Ferrite\session.json` (open files and panes). Containers keep their data under `%LOCALAPPDATA%\Ferrite\containers`.

### Which profile does Ferrite run?

Your normal PowerShell profiles, plus `Microsoft.FERRITE_profile.ps1` for Ferrite-only settings and `$psIDE` add-ons. A container has its own profile folder instead.

### Is a container a security boundary?

The default *separate profile* mode keeps tokens, secrets, history and modules apart, but runs as your Windows user: Credential Manager, the certificate store, HKCU and DPAPI keys are shared. For full isolation use a **Windows Sandbox** container. See [Containers](Containers.md).

### Import-Module loads the wrong version, or two modules won't load together.

Open the **Modules** pane (View > Show Modules) and use **Fix all** in the conflicts section. See [Modules](Modules.md#conflicts-and-fix-all).

### The Claude pane says `claude` was not found.

The Claude pane is optional and needs [Claude Code](https://claude.com/claude-code). The pane shows the install command, and *Browse for claude...* if it's installed somewhere Ferrite doesn't look. Ferrite never installs it for you.

### How do I see what's new?

**Help > Welcome to Ferrite** shows the notes for your version, with earlier releases below. The Welcome page also opens once after every update.

### How do I stop the Welcome page from opening?

Untick **Show at startup** at the bottom of it. It then stays closed, also after updates; Help > Welcome to Ferrite opens it any time.

### How do I report a bug or a security problem?

Bugs: open an issue in [this project](https://github.com/Shoqu-TMGCLD/Ferrite-releases/issues) and include the version from **Help > About**.

Security problems: please report them privately with [Report a vulnerability](https://github.com/Shoqu-TMGCLD/Ferrite-releases/security/advisories/new), not as a public issue.

### Is Ferrite built with AI?

Ferrite is developed with the help of Claude Code, Anthropic's AI coding assistant. The maintainer directs and tests the work.
