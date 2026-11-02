# Changelog

## 0.1.1 (2026-11-02)

- **`hushjot`:**
  - `Notes::update_if_unchanged` writes a note's text only while it still holds the text the editor last read, as one step with the sync, and returns `ConditionalUpdate::Changed` (or `Deleted`) otherwise. An editor holding unsaved text while another device's edit arrives no longer has to choose between writing over it and losing its own.
  - Fixed: a pull that landed between a local write's read and its write (an edit, pin, move, delete, restore, undelete or a folder's delete) was overwritten unseen. Those writes, and the sync's application of a pulled note and settling of a conflict, now hold one write guard; the vault's write helpers take only rows read under it.
  - Fixed: a text edit made while a pin's or move's push was on the network, when that push then met another device's edit, was replaced by the other device's text without a conflict copy. Settling the conflict now reads the note again under the write guard.
- Update dependencies to the latest versions: aes-gcm 0.11, argon2 0.6, hkdf 0.13 and sha2 0.11 (RustCrypto's digest 0.11 generation), getrandom 0.4, base64 0.23 and rusqlite 0.41. No change to the format or the API.

## 0.1.0 (2026-10-31)

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
