# Modules

## The Modules pane

**View > Show Modules** opens the Modules pane on the right. It lists every installed module, grouped by name, with:

- the newest version, how many versions are installed and whether an update is available
- where each copy loads from: Current user, All users, Built-in, Container, Project or another path
- size on disk, signer and repository for each version

Search by module name or exported command, and filter by location, updates or multiple versions. The toolbar has **Refresh**, **Check updates**, **Loaded?** (which modules the current session has loaded) and **Install…**.

The inventory runs in a separate background PowerShell process, never in your console, so it doesn't slow your session down. The last result shows at once and is refreshed in the background.

## Install, update, uninstall

These use PSResourceGet. Every change opens a confirmation listing exactly what will happen.

- **Install…**: search by name or command, then install for the current user, for all users, or into a container's module folder
- **Update to x.y** on a module row
- **Remove N old version(s)** keeps the newest copy
- **Uninstall** a single version

Changes for **all users** need administrator rights: that one operation shows a Windows UAC prompt. Ferrite never deletes modules under `C:\Windows`, `$PSHOME` or a `PSModulePath` root folder.

Repositories are listed in the pane too: trust or unregister them, or register a private NuGet feed.

## Conflicts and Fix all

Ferrite looks for two kinds of conflict:

- **Shadowing**: `Import-Module` loads an older copy because it comes first on `PSModulePath`, although a newer one is installed.
- **Shared assemblies**: modules that ship different versions of the same DLL (MSAL, Azure.Identity, Newtonsoft.Json, Microsoft Graph core and others). Whichever loads first wins, so the other may fail. Typical example: Microsoft Graph, Exchange Online and dbatools in one session.

**Fix all** in the conflicts section:

- removes older copies that hide newer versions
- updates modules that ship older shared DLLs
- turns on a load-order fix, so those modules load together in one session

You confirm the changes before they run. Conflicts are also reported once per session in the Output pane, and `Import-Module` lines that would load the older DLL first get a warning in the editor.

## Help in the editor

- A command that no installed module provides gets a squiggle. Right-click > **Find module for 'X'…** searches for it and offers to install the module.
- `#Requires -Modules` entries that are missing or too old get **Install module 'X'…**.

## Module sets

A **module set** pins the modules of a container or a project, reproducibly, without touching your normal module folders.

- **Manifest** `ferrite.modules.psd1`: module names with version ranges (`'[2.25.0,3.0)'`, `'3.7.1'` for "this or newer", `'*'` for newest) and optional private repositories.
- **Lock file** `ferrite.modules.lock.json`: exact versions and SHA-256 hashes. *Restore* installs exactly the lock and refuses a package whose hash doesn't match; *Update lock* picks the newest versions within the ranges.

```powershell
@{
    Modules = @{
        'Microsoft.Graph.Authentication' = '[2.25.0,3.0)'
        ExchangeOnlineManagement         = '3.7.1'
        Pester                           = '*'
    }
}
```

**Containers**: Containers manager > *More* > *Modules…* edits the container's set. When the container opens, missing modules are restored in the background. (Windows Sandbox containers don't support module sets.)

**Projects**: when a script's folder (or a parent) contains `ferrite.modules.psd1`, a bar above the editor offers to install the modules into the current workspace. Commit the lock file with the project.

Downloaded packages are cached once in `%LOCALAPPDATA%\Ferrite\cache\nupkg` for all containers and projects. Nothing is installed into your real CurrentUser or AllUsers module folders.

## Signing policy

In a container, the Modules pane's **Allowed modules** setting can allow any module, only signed modules, or only modules signed by publishers you list, and either warn or block the import.

## Modules in OneDrive

If your Documents folder syncs to OneDrive, module folders there can be slow or locked. The pane shows a banner with **Move user modules out of OneDrive…**, which moves them to `%LOCALAPPDATA%\PowerShell\Modules` and updates your `PSModulePath`. **Undo move…** puts everything back.
