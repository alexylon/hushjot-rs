# Changelog

## Unreleased

- Update dependencies to the latest versions: aes-gcm 0.11, argon2 0.6, hkdf 0.13 and sha2 0.11 (RustCrypto's digest 0.11 generation), getrandom 0.4, base64 0.23 and rusqlite 0.41. No change to the format or the API.

## 0.1.0 (unreleased)

First release. The emulator journey runs against the app's live rules.

- **`hushjot-core`:**
  - Envelope v1 and v2, key records, Argon2id and HKDF unlock.
  - Note meta, folder and share JSON.
  - Titles, excerpts and list order.
  - The folder tree and tags.
  - The search grammar, index and phrase verification.
  - Metering arithmetic, history policy and share links.
- **`hushjot`:**
  - Sign-in and session refresh, and the Firestore REST protocol.
  - SQLite and memory stores, OS-keychain secrets.
  - A local-first vault: notes, folders, history, shares and search.
  - The sync engine, with conflict copies, metadata rebase, limits and pauses.
  - Offline launch: `resume` and unlocking work without the network once the device has been online.
- **Integration guide:** closing the app without losing edits or writing plaintext, and opt-in rules for AI agents.
- **Examples:** `quickstart`, and `mini_editor`, a terminal editor covering the whole SDK (walkthrough in `docs/mini-editor.md`).
