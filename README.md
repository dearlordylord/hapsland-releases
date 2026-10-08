# Hapsland releases

**Purpose:** Distribute verified ready-made Hapsland packages.
**Status:** Maintained distribution guidance.
**Authority:** Maintained guidance; published artifacts and their checksums identify each release. Offline package checks do not establish every agent-runtime compatibility profile.
**Expected use:** Install the platform package or verify a downloaded release.
**Lifecycle:** Update with each public release and installation-channel change; remove superseded instructions.

Hapsland integrates configurable code review with coding agents. This repository contains ready-made release assets, not the private source checkout.

## Install with Homebrew

On macOS arm64 or Linux arm64:

```sh
brew install dearlordylord/tap/hapsland
hapsland setup
```

Hapsland includes Bun and its native assets; no external Node/Bun or source build is needed. Git and your coding agent must be available. Setup previews integration changes and asks before installing hooks. Jev credentials, when needed, belong in the masked setup prompt, not in chat. Package installation and offline checks make no review-provider request.

Update the package with `brew upgrade dearlordylord/tap/hapsland`. Updating package bytes and activating hooks in an agent profile are separate actions; use the package's setup/update guidance.

## Download directly

Select the matching macOS (`darwin-arm64`) or Linux (`linux-arm64`) archive from [Releases](https://github.com/dearlordylord/hapsland-releases/releases), together with `SHA256SUMS`.

On macOS, verify the selected file with `shasum -a 256` and compare its digest to the matching line in `SHA256SUMS`; on Linux use `sha256sum`. Extract the archive and keep the entire `package/` directory intact. From the Git repository you want reviewed, run `/absolute/path/to/package/bin/launch.sh setup`.

Worker bundles, native helpers, rules, schemas and other runtime resources belong to the installation. Do not copy only the executable. The archive does not register commands in PATH or install agent hooks by itself.

Each release carries `distribution.json`, tying platform archives to the source candidate, audited npm archive and audit digest. Platform packaging preserves the audited file bytes and modes; it does not rebuild or change the executable layout.

Current build targets are macOS arm64 and Linux arm64. Installed package and parser checks are offline evidence, not a declaration that every coding agent or version is supported. Consult the compatibility documents included in the package.
