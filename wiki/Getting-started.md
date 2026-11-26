# Getting started

## Requirements

- Windows 10 or 11 (x64)
- [PowerShell 7.4 or later](https://learn.microsoft.com/powershell/scripting/install/installing-powershell-on-windows) (`pwsh`)

## Install

Download `Ferrite-<version>-x64.msi` from the [latest release](https://github.com/Shoqu-TMGCLD/Ferrite-releases/releases/latest) and run it. Ferrite installs into `Program Files\Ferrite`, adds a Start menu shortcut and an **Edit with Ferrite** entry for `.ps1`, `.psm1` and `.psd1` files. After that it [updates itself](Updates.md).

The first time Ferrite starts it opens the **Welcome** page. It opens again once after every update to show what changed. Reopen it any time with **Help > Welcome to Ferrite**.

## The window

- **Script pane**: one tab per script. **File > New** (Ctrl+N), **Open** (Ctrl+O), **Save** (Ctrl+S). Files dropped on the window open too.
- **Console pane**: the PowerShell session of the current tab.
- **Side panes**: View > Show Command Add-on, Show Variables, Show Outline, Show Modules. Bottom panes: Show Output, Show Breakpoints, Show Call Stack.
- **PowerShell tabs**: above the script tabs. Each one is its own PowerShell session with its own scripts and console.

Ctrl+1 / Ctrl+2 / Ctrl+3 put the script pane on top, on the right, or maximized. Ctrl+R shows or hides it.

## Run a script

| Key | What it does |
|---|---|
| F5 | Run the whole script (file-backed scripts are saved first). Continues when stopped at a breakpoint. |
| F8 | Run the selection, or the current line when nothing is selected |
| Ctrl+Break | Stop the running command |

Everything runs in the console of the current PowerShell tab, so variables and functions stay defined between runs.

## Debug

F9 toggles a breakpoint on the current line. Press F5 to run. When Ferrite stops, step with F10 (over), F11 (into) and Shift+F11 (out); Shift+F5 stops the debugger. The **Variables** and **Call Stack** panes show the current state. The **Debug** menu adds command breakpoints, conditions, hit counts and log points.

## Console modes

**View > Console Mode** switches the console between:

- **Terminal**: a real terminal (ConPTY) with colours and PSReadLine.
- **Classic**: the ISE's output pane with an input line below it (Up/Down for history, Shift+Enter for a new line).

You can switch at any time; the choice is remembered.

## PowerShell tabs

- **Ctrl+T**: new local PowerShell tab
- **Ctrl+Shift+R**: new remote tab over WinRM or SSH (credentials are asked for in the console)
- **Ctrl+W**: close the tab

**Shift+click** the **+** tab button to create a [container](Containers.md) instead.

## Settings

**Tools > Options** sets the theme (Light, Dark or System), fonts, colours, console mode, tab size, script analysis and the paths to `pwsh` and PowerShell Editor Services. Settings are saved in `%APPDATA%\Ferrite\settings.json`. Open scripts are restored at the next start, and unsaved changes are kept for crash recovery.

## Your profile and add-ons

Ferrite runs `Microsoft.FERRITE_profile.ps1` from your PowerShell profile folder (`$HOME\Documents\PowerShell`). Scripts there can use the `$psIDE` object, as in the ISE:

```powershell
$psIDE.CurrentFile          # the active script
$psIDE.Editor.SelectedText  # the selection
$psIDE.CustomMenu.Add('Insert date', { $psIDE.Editor.InsertText((Get-Date).ToString('yyyy-MM-dd')) }, 'Ctrl+Alt+D')
```

Custom items appear in the **Add-ons** menu.

## Keyboard shortcuts

| Key | Action | Key | Action |
|---|---|---|---|
| Ctrl+N / O / S | New / Open / Save | F5 | Run script / Continue |
| Ctrl+Shift+S | Save As | F8 | Run selection / line |
| Ctrl+F4 | Close script tab | Ctrl+Break | Stop |
| Ctrl+T | New PowerShell tab | F9 | Toggle breakpoint |
| Ctrl+Shift+R | New remote tab | Ctrl+Shift+F9 | Remove all breakpoints |
| Ctrl+W | Close PowerShell tab | Ctrl+Shift+L | List breakpoints |
| Ctrl+F / H / G | Find / Replace / Go to line | F10 / F11 / Shift+F11 | Step over / into / out |
| F3 / Shift+F3 | Find next / previous | Shift+F5 | Stop debugger |
| Ctrl+Space | IntelliSense | Ctrl+Shift+D | Call stack |
| Ctrl+J | Snippets | Ctrl+D / Ctrl+I | Focus console / script |
| Ctrl+M | Toggle all outlining | Ctrl+R | Show/hide script pane |
| Ctrl+Plus / Minus / 0 | Zoom | Ctrl+1 / 2 / 3 | Script top / right / maximized |
| F1 | Get-Help for the word at the caret | Ctrl+F1 | Show command (Commands pane) |
| F12 | Go to definition | Ctrl+K / Ctrl+U | Comment / uncomment |
| Ctrl+Shift+F | Format document | Alt+drag | Box selection |
| Ctrl+Shift+0..9 | Switch workspace | Ctrl+Shift+A | Ask Claude about the selection |
