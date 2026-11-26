# Features

## Script editor

- Syntax highlighting with the ISE's colours, brace matching, auto-indent, block indent with Tab / Shift+Tab
- IntelliSense (Ctrl+Space, and automatically after `-`, `.`, `$` and `::`), signature help, hover help, go to definition (F12), rename
- Code folding for braces, `#region`, here-strings and comment blocks (Ctrl+M toggles all)
- Find and replace with match case, whole word, regular expressions and in-selection; go to line
- Snippets (Ctrl+J), comment / uncomment (Ctrl+K / Ctrl+U), format document (Ctrl+Shift+F), expand aliases
- PSScriptAnalyzer squiggles and quick fixes (turn off in Tools > Options)
- Box selection with Alt+drag, line numbers, word wrap, zoom
- UTF-8 with BOM for new files; existing encodings and CRLF line endings are kept
- A prompt when a file changes on disk, and crash recovery for unsaved scripts

## Console

Two modes, switched with **View > Console Mode**:

- **Terminal**: a real terminal (ConPTY) with colours, PSReadLine, selection and scrollback
- **Classic**: the ISE output pane with coloured errors, warnings and verbose output, and an input line with history

The console is the same PowerShell session that runs your scripts and the debugger.

## Run and debug

- F5 runs the script, F8 the selection or the current line, Ctrl+Break stops
- Line, command and variable breakpoints, with conditions, hit counts and log points
- Step over / into / out, call stack, and the Variables pane while stopped

## Panes

- **Commands** (View > Show Command Add-on): search commands, filter by module, fill in a parameter form, then Run, Insert or Copy. Ctrl+F1 opens it for the word at the caret.
- **Variables**: the session's variables, live; the debugger's scopes when stopped
- **Outline**: functions and regions of the current script
- **Output**: messages from the language service and from Ferrite's background jobs
- **Breakpoints** and **Call Stack**
- **Modules**: see [Modules](Modules.md)

## PowerShell tabs

Several PowerShell sessions side by side, each with its own scripts and console. Ctrl+T opens a local tab, Ctrl+Shift+R a remote tab over WinRM or SSH.

## Containers

Colour-coded workspaces with their own profile, module path, history and credentials, so work for different clients or tenants stays apart. Containers can be temporary, and there is an optional Windows Sandbox mode. See [Containers](Containers.md).

## Module management

An inventory of every installed module and where it loads from; install, update and uninstall through PSResourceGet; conflict detection with **Fix all**; module sets per container or project with lock files; signing policies per container. See [Modules](Modules.md).

## Add-ons

- **`$psIDE`** scripting API in `Microsoft.FERRITE_profile.ps1`: the current file, open files, editor text and selection, custom menu items with shortcuts.
- **Claude pane** (optional): runs [Claude Code](https://claude.com/claude-code) next to your scripts when the `claude` command is installed. Open it with **Add-ons > Claude > Show Claude Pane** or **View > Show Claude**. Ask about the selection (Ctrl+Shift+A), explain the last console error, fix a script, or write a Pester test, from the Add-ons > Claude menu or the editor's right-click menu. Dock it at the bottom, left or right, or in its own window, with its **Move** menu or by dragging its grip. Claude can read your open scripts through Ferrite's MCP server; edits and runs need your approval in Ferrite. Each container gets its own Claude sign-in and settings.

## Look and feel

Light, Dark or System theme, ISE keybindings, three pane layouts (Ctrl+1/2/3), session restore and crash recovery.

## Updates

Ferrite checks for new versions and installs them after you confirm. See [Updates](Updates.md).
