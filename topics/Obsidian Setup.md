#index #obsidian #pkm #wiki #setup

## Vault Info
- **Location:** `/home/hermes/obsidian-vault/`
- **Managed by:** Hermes Agent + Yura (local Obsidian app)
- **Sync:** Manual (no auto-sync configured yet)

## How It Works
1. Yura uses **Obsidian app** on Mac/PC/phone
2. Hermes Agent reads/writes notes via file system at `/home/hermes/obsidian-vault/`
3. Both can access the same notes — real-time when synced

## Syncing Options

### Option A: Obsidian Sync (Recommended)
- $4/month for unlimited
- Built-in, seamless
- Yura just needs to enable it on his device

### Option B: Git Sync
- Free via Obsidian Git plugin
- Auto-commit on change
- Needs git setup

### Option C: iCloud / Dropbox
- If Yura is on Mac/iOS
- Files live in cloud folder, Obsidian opens vault there

### Option D: Manual Sync
- Yura periodically syncs the `/home/hermes/obsidian-vault/` folder to his local machine
- No auto-sync — manual effort

## Recommended Plugins

| Plugin | Purpose |
|--------|---------|
| **Templater** | Dynamic templates with JS/Templater syntax |
| **Dataview** | Query notes like a database |
| **Obsidian Git** | Auto-commit changes to git |
| **Banners** | Nice header images |
| **Minimal Theme** | Clean, distraction-free |
| **Quick Add** | Fast capture shortcuts |
| **Shell Commands** | Run shell from Obsidian |

## Folder Structure
```
obsidian-vault/
├── inbox/          # Quick captures
├── log/            # Daily & session logs
├── projects/       # Active projects
├── people/         # Contacts
├── topics/         # Deep dives
├── notes/          # Atomic notes
├── _templates/     # Note templates
├── _scripts/       # JS automation
└── _assets/        # Images, files
```

## Tags System
```
#daily         — daily note
#project       — active project
#person        — contact
#topic         — deep dive
#idea          — unvalidated idea
#resource      — reference
#question      — open question
#insight       — learned something
#hermes        — related to Hermes setup
#ai            — AI-related
```

## Working with Hermes
Yura can say things like:
- "Save this to Obsidian: [thought]"
- "What notes do we have about [topic]?"
- "Update [note] with [content]"
- "Create a new note about [topic]"

Hermes will read/write to the vault and link notes properly.

## Status
✅ Vault created: 2026-07-03
✅ Templates set up
✅ Hermes can read/write
⬜ Yura to install Obsidian app and connect vault
⬜ Sync method to be chosen

---
*Last updated: 2026-07-03*
