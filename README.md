# homebrew-reelm

Homebrew tap for [Reelm](https://github.com/Woodman11/youtube-search) — a local Chrome extension + Python server that saves YouTube videos and indexes their transcripts in SQLite FTS5.

## Install

```bash
brew tap Woodman11/reelm
brew install reelm
brew services start reelm
```

Then load the bundled Chrome extension (one-time):

1. Open `chrome://extensions`
2. Enable **Developer mode** (top right)
3. Click **Load unpacked** → select the path printed in `brew info reelm`'s caveats (`#{libexec}/extension`)

Press **Shift+Y** on any YouTube video to save it, then click the extension icon to search across saved transcripts.

## What gets installed

| Command | Purpose |
|---------|---------|
| `reelm` | CLI search (`reelm "query"`) |
| `reelm-server` | The local HTTP server on `localhost:7799` (auto-started by `brew services`) |
| `reelm-maintain` | Retries failed transcripts, optimizes FTS5, rotates logs |

The DB lives at `~/Library/Application Support/Reelm/videos.db`. On upgrade from older versions, an existing `MyYouTubeSearch/` DB is migrated automatically on first run.

## Updating

```bash
brew update
brew upgrade reelm
brew services restart reelm
```
