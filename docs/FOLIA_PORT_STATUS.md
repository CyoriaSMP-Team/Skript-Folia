# CyoriaSMP Skript 2.17 Folia port — experimental

This feature branch is a **development port**, not a production release.
It applies the region-aware scheduler strategy from the GPL-licensed SkriptFolia 2.16 port to the CyoriaSMP-Team/Skript-Folia 2.17 source, adapting newer command registration and command effects. It keeps the original CyoriaSMP repository as the source of truth.

## Verified locally on 20 October 2026

- `./gradlew compileJava` and `./gradlew shadowJar` succeeded on Java 25.
- Dedicated disposable Folia 1.21.11 build 14 server loaded Skript 2.17.
- Loaded 5,684 aliases and a tiny script containing `on load` and a command; no script parse errors.
- `on load` executed. Graceful server shutdown unloaded Skript without exceptions.
- The standalone test JAR SHA-256: `d5ca1614f3ec1bd2baefd4bb76609c0b006bfa5ca87fc9f9ac521cc935518b27`.
- CyoriaSMP production was not changed or restarted by this branch's development.

## Not verified / known limitations

- No tests yet with the server's existing Skript scripts, SkBee, skript-reflect, skript-db, or other addons.
- Player click events, async chat, player disconnects, cross-region teleports, multiple regions, block/furnace operations, entity ownership, and command sync under heavy load are untested.
- Some upstream Skript 2.17 code paths still reference the Bukkit scheduler directly (including `ScriptCommand`, `IndeterminateDelay`, `EvtRealTime`, and other world-specific effects); they must be audited and converted to a matching region/entity scheduler before production use.
- CI success alone is not proof of Folia runtime safety.

Do **not** merge into master (which auto-releases) or install in the production server until the remaining safety and integration checks are completed.
