# Omarchy Magazine Covers

A high-fidelity weekly magazine cover artwork viewer for [Omarchy Linux](https://omarchy.org), built as a native Wayland bar widget and keyboard-first popup panel using Quickshell (QtQuick / QML) and Python.

Browse the latest issues, headlines, and the last 5 weekly covers for premier publications with razor-sharp artwork and zero third-party dependencies.

---

## Supported Publications

| Publication | Frequency | Source Focus | Default Accent |
| :--- | :--- | :--- | :--- |
| **The Economist** | Weekly (Saturdays) | Global edition cover art & issue lead title | `#E51C1C` |
| **The New Yorker** | Weekly (Mondays) | Iconic cover illustrations, artist bylines & stories | `#D97706` |
| **Barron's** | Weekly (Mondays) | Authentic financial magazine print covers & headlines | `#2563EB` |
| **Newsweek** | Weekly (Fridays) | Archive high-resolution front page covers | `#E10600` |

---

## Features

- **Large, Crisp Cover Art**:
  - Downsampled with `mipmap: true` and `smooth: true` to prevent aliasing and ensure all cover text, headlines, and dates are crystal clear.
  - Hover navigation arrows (`<` and `>`) overlay directly on the artwork for rapid browsing.
  - One-click full-resolution viewing: click any cover or the **Full Res** button to open the original image in your system viewer (`imv`) for instant pan and zoom.

- **Last 5 Covers Interactive Strip**:
  - Horizontal thumbnail carousel of the 5 most recent weekly editions with date labels.
  - Highlighted with publication brand colors and elevation styling.
  - Clicking any thumbnail immediately transitions the hero display.

- **Zero-Overflow Responsive Layout**:
  - Predictable `ColumnLayout` budgeting designed to fit inside the panel on any display scaling without awkward clipping or scrollbars.

- **Discord Webhook Sharing**:
  - One-click (or hotkey `D`) posting of the currently selected cover artwork and headline directly to your configured Discord channel.

- **100% Python Standard Library**:
  - Zero `pip` packages, zero external libraries (`urllib.request`, `ssl`, `json`, `re`, `datetime`, `html`, `hashlib`). Runs turnkey on any distribution out-of-the-box.

---

## Keyboard Navigation

When the panel is open:

| Key | Action |
| :--- | :--- |
| <kbd>Left</kbd> / <kbd>h</kbd> | Previous cover |
| <kbd>Right</kbd> / <kbd>l</kbd> | Next cover |
| <kbd>1</kbd> | Switch to **The Economist** |
| <kbd>2</kbd> | Switch to **The New Yorker** |
| <kbd>3</kbd> | Switch to **Barron's** |
| <kbd>4</kbd> | Switch to **Newsweek** |
| <kbd>Tab</kbd> / <kbd>Shift+Tab</kbd> | Cycle through publications |
| <kbd>Enter</kbd> / <kbd>o</kbd> | Open full issue/article in default browser |
| <kbd>v</kbd> / <kbd>Space</kbd> | Open high-resolution image in image viewer (`imv`) |
| <kbd>d</kbd> | Share cover to Discord |
| <kbd>r</kbd> | Force-refresh covers from sources |
| <kbd>Esc</kbd> | Close panel |

---

## Installation

### 1. Clone into your projects directory
```bash
git clone https://github.com/visual-zimbabwe/omarchy-magazine-covers.git ~/Projects/omarchy-magazine-covers
```

### 2. Link or copy to Omarchy plugins
```bash
mkdir -p ~/.config/omarchy/plugins
ln -s ~/Projects/omarchy-magazine-covers ~/.config/omarchy/plugins/juwimana.economist
```

### 3. Enable in `~/.config/omarchy/shell.json`
Add `juwimana.economist` to your bar layout (e.g., in the right section):
```json
{
  "bar": {
    "layout": {
      "right": [
        { "id": "juwimana.economist" }
      ]
    }
  }
}
```

### 4. Restart the Omarchy Shell
```bash
omarchy restart shell
```

---

## CLI Usage

The backend fetcher can be tested and run directly from the command line:

```bash
# Get cached covers JSON (or fetch if stale)
./economist-fetch json

# Force re-fetch and refresh all cover artwork
./economist-fetch refresh

# Share currently selected cover to Discord
./economist-fetch discord --source economist --index 0
```

---

## Configuration

Configuration is stored at `~/.config/omarchy/economist.json`:

```json
{
  "discord_webhook": "https://discord.com/api/webhooks/YOUR_WEBHOOK_URL",
  "active_source": "economist"
}
```

Cached cover art is downloaded to `~/.local/state/omarchy/economist/covers/`.

---

## License

MIT © [juwimana](https://github.com/visual-zimbabwe)
