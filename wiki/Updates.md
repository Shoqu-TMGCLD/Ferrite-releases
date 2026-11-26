# Updates

Ferrite updates itself from the [releases of this project](https://github.com/Shoqu-TMGCLD/Ferrite-releases/releases).

## How it works

Once a day at startup Ferrite asks GitHub for the latest release, and **Help > Check for Updates** checks right away. When a newer version is available, a bar at the top of the window offers **Update now**, the release notes, **Skip this version** and **Later** (hide the bar until the next start).

**Update now**:

1. downloads the installer and checks its SHA-256 (and, for signed releases, its signature and publisher)
2. closes Ferrite the normal way: your session is saved and you're asked about unsaved scripts
3. installs the update (one Windows administrator prompt)
4. opens Ferrite again

If the hash or signature doesn't match, the download is deleted and nothing is installed.

After an update, Ferrite opens the **Welcome** page once to show what's new in the version you now have. **Help > Welcome to Ferrite** shows it again.

## Turn off the daily check

Untick **Help > Check for Updates Automatically**. You can still check by hand.

## Install a version by hand

Download `Ferrite-<version>-x64.msi` from [Releases](https://github.com/Shoqu-TMGCLD/Ferrite-releases/releases) and run it. Your settings and sessions are kept.

## What Ferrite connects to

Only GitHub, over HTTPS: the GitHub API for release information, and `github.com` / `*.githubusercontent.com` for the installer. No sign-in is needed.
