# repovet-canary

**A test fixture for [RepoVet](https://repovet.dev). It contains no malware.**

Like the EICAR test file for antivirus software, this repository holds harmless
files that *look* like malware indicators, so RepoVet should report it as
**malware found**. If a scan of this repository ever comes back clean, detection
is broken.

Nothing here downloads, installs or runs anything harmful. Every "suspicious"
file is inert text. Still: **do not run `npm install` in `fixtures/`**, because
that folder names a package that was really published to npm as malware.

## What each file tests

| File | RepoVet check | Expected finding |
|---|---|---|
| `src/canary.js` | Signatures | `repovet.canary`: RepoVet's own test marker (critical) |
| `tailwind.config.js` | Obfuscation, entropy | code hidden after a run of spaces, `eval(`, a `child_process` import and a random base64 blob in a build config |
| `public/fonts/canary.woff2` | Fonts | a "font" that is really plain text (critical) |
| `.vscode/tasks.json` | Auto-run | a task that runs when the folder is opened (it only echoes text) |
| `fixtures/package.json` | Packages | depends on a known malicious npm package name (critical), plus an install hook |
| `temp_auto_push.bat` | Known file names | a helper-script name used by PolinRider (it only echoes text) |
| `.gitignore` | Auto-run | hides `config.bat`, as PolinRider does |

The real PolinRider marker strings are deliberately **not** used, so this
repository does not show up in public lists of infected projects.

[![RepoVet](https://repovet.dev/badge/github/nezar-madi/repovet-canary.svg)](https://repovet.dev/github/nezar-madi/repovet-canary)
