# Containers

A **container** is a separate, colour-coded workspace. Its PowerShell sessions get their own profile folders, so sign-in tokens, saved secrets, module folders and command history stay apart from your normal workspace and from other containers. Use one per client, tenant or project.

## Create one

- **Shift+click** the **+** button next to the PowerShell tabs, or
- **File > New Container...**, or
- **+ Container** in the workspace switcher

Pick a name, a colour, the isolation mode and whether it is persistent or temporary.

## Switch and manage

The **Workspace** strip above the PowerShell tabs lists *Default* and every open container, an *Open* menu for closed ones, and *Manage…*. **Ctrl+Shift+0** switches to Default and **Ctrl+Shift+1..9** to the open containers. Container tabs show the container's colour and name, and the window title shows `[Name]`.

**View > Containers...** opens the **Containers manager**: open, close, rename and recolour containers, set environment variables and a startup script, open the data folder, see disk usage, wipe data or delete a container.

Each container has its own PowerShell tabs, scripts, recent files, breakpoints and session restore. Workspaces you switch away from keep running.

## What is kept apart

**Separate profile** (the default): `USERPROFILE`, `HOME`, `APPDATA`, `LOCALAPPDATA` and `TEMP` point into the container, so these land in the container:

- Microsoft authentication token caches (used by Az and Microsoft Graph)
- SecretStore vaults
- PSReadLine history
- `$PROFILE` and the container's own module folder (first on `PSModulePath`)
- Git Credential Manager, Azure CLI, AWS, .NET/NuGet, npm and Claude Code settings

**Not kept apart** (they belong to your Windows account): DPAPI keys, Windows Credential Manager, the certificate store, the HKCU registry and the Documents folder. Ferrite warns once when a command in a container uses Credential Manager, `HKCU:` or `Cert:\CurrentUser`.

**Windows Sandbox** (Windows 11 24H2 or later, with the Windows Sandbox feature turned on): the console runs inside a disposable Sandbox virtual machine. Ferrite sets up PowerShell 7 in it and connects over PowerShell remoting; F5, F8 and Ctrl+Break run in the VM. The VM is always discarded when the container closes; *Persistent* keeps only the shared `C:\Ferrite` folder and the container's settings. Only one Sandbox can run at a time. If the feature is missing, Ferrite shows how to turn it on.

## Persistent or temporary

- **Persistent**: data is kept, and containers that were open reopen at the next start (Sandbox containers are not reopened automatically).
- **Temporary**: all data is deleted when its last tab closes, when Ferrite exits, or at the next start if Ferrite crashed.

## Module sets

A container can pin its modules with a module set (Containers manager > *More* > *Modules…*). See [Modules](Modules.md#module-sets).

## Command line

```powershell
ferrite --container=ClientA   # start in the ClientA container
ferrite --containers          # open the Containers manager at start
```

## Where data lives

- List of containers: `%APPDATA%\Ferrite\containers.json` (no secrets)
- Container data: `%LOCALAPPDATA%\Ferrite\containers\<id>\`
