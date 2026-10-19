**English** · [Türkçe](README.tr.md) · [Deutsch](README.de.md) · [Español](README.es.md)

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.png">
    <img src="assets/logo-light.png" alt="modsweep" width="460">
  </picture>
</p>

<p align="center"><b>Clean Projects. Keep Building.</b><br>
Find, analyze and safely clean <code>node_modules</code> in your JavaScript projects — a native macOS app.</p>

<p align="center">
  <a href="https://github.com/caglarergul/modsweep-macos/releases/latest"><b>Download the latest version</b></a>
  · macOS 14 Sonoma or later · Apple Silicon and Intel
</p>

---

## Install

**Download:** get `modsweep-<version>.dmg` from the [latest release](https://github.com/caglarergul/modsweep-macos/releases/latest),
open it and drag **modsweep** to **Applications**. Every build is signed with Developer ID and notarized by Apple, so
it opens without warnings.

**Homebrew:**

```bash
brew install --cask caglarergul/tap/modsweep   # install
brew upgrade --cask modsweep                   # update
brew uninstall --cask --zap modsweep           # remove the app and its data
```

**Requirements:** macOS 14 Sonoma or later. Installing projects (Install & verify) needs
[pnpm](https://pnpm.io/installation); npm, yarn and bun projects are handled too.

## What it does

| | |
|---|---|
| **Scan** | Finds the JavaScript projects in a folder and shows how much space each `node_modules` takes, the package manager, last activity and git state, plus npm/pnpm/yarn/bun caches and free disk. The total sits in the menu bar. |
| **Analyze** | Finds install and run problems before they hit you — lockfiles out of sync, two lockfiles, Node version mismatches, `node-sass`, old webpack on new Node, Next 16 with a webpack config, Prisma, missing `.env`, Stencil store problems … — and suggests a fix for each. |
| **Clean** | Moves the `node_modules` folders you pick to the **Trash**, so you can put them back. Folders with a running Node process or files tracked by git are left alone. |
| **Install & verify** | Installs the selected projects and checks dependencies, commands, typecheck, build and optionally a dev server — with a live log, a Stop button and everything restored afterwards. |

Available in **English, Türkçe, Deutsch and Español** (Settings → Language).

## Safety

modsweep is made for real projects that are connected to live systems.

- **Nothing is pushed or deployed.** Scripts that mention deploy, publish, push, migrate, vercel, shopify … never run
  during a test.
- **Databases are unreachable.** Database, Redis and Mongo addresses from `.env` files point nowhere while testing.
- **Your files are restored.** `package.json`, lockfiles and the git state are backed up before a test and put back
  afterwards — also when you press Stop.
- **No process is left behind.** Test servers are stopped by process tree and by folder.
- **Crash-safe.** If the Mac or the app stops in the middle of a test, modsweep restores the project the next time it
  starts, before doing anything else.
- **Clean goes to the Trash.** Nothing is deleted permanently by the app.

## First launch

modsweep suggests your home folder but scans nothing on its own. Choose the folder that holds your projects (for
example `~/Developer` or `~/www`) and press Scan. You can change it any time in the sidebar or in Settings.

If your Node, pnpm or other tools come from nvm, asdf or mise, add their folder in **Settings → Tools**.

## Privacy

modsweep has no account, no analytics and no tracking. It only goes online when you ask it to: installing packages
during Install & verify, and the optional Stencil store check in the analysis (can be turned off in Settings).

## Uninstall

`brew uninstall --cask --zap modsweep`, or drag modsweep from Applications to the Trash and remove
`~/Library/Application Support/modsweep`.

## Disclaimer

modsweep is free and provided "as is", without warranty. It changes files on your computer (Trash, package
installs, builds); you use it at your own risk. Keep backups and version control. Read the full
[disclaimer](DISCLAIMER.md).

---

This repository only hosts the release files; the source code is not public.

Copyright © 2026 Caglar Ergul. All rights reserved.
