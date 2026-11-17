# mycall database updates

This repository hosts signed, encrypted database updates for mycall. Downloading
updates requires no GitHub account. The Android app checks and verifies releases
using its bundled public key before applying them.

Each release contains exactly three assets:

- `manifest.json`: the database package size, SHA-256, revision and original snapshot metadata.
- `manifest.sig`: an ECDSA P-256 / SHA-256 signature in DER format over the exact manifest bytes.
- `mycall-db-<sequence>.zip`: the encrypted `main.sqlite` and `instant.sqlite` databases.

The databases remain encrypted. This repository contains no application source,
private signing key or user data. The app keeps local messages, rules and caches
on the device.

The first release, `db-2026-11-17.1` (sequence `2026111701`), hosts the existing
2026-11-15 snapshot: 42,097 main records and one instant record. This first release
establishes the update channel; it does not introduce newer source data. Apps that
already have this snapshot can report that their data is current.

Database updates require mycall version code 14 or later. Manual updates ask for
confirmation before applying. Automatic updates are off by default and use Wi-Fi
by default when enabled.
