# firefox-round-userchrome

A compact, floating Firefox UI: 32px tab bar, an address bar and bookmarks bar that slide in over the page on hover, frosted-glass styling, and icons for the tab context menu. Updated for **Firefox 160**.

Based on **[My round userChrome](https://gitlab.com/markonius/my-round-userchrome)** by markonius. This version has drifted a long way from the original, but that's where it started, so credit goes there. The original has no license file. If you're the author and want this changed or taken down, open an issue.

## Install

1. Open `about:support` and click **Open Folder** next to *Profile Folder*.
2. Copy `userChrome.css` into a `chrome` folder inside it (create the folder if it doesn't exist).
3. Copy `user.js` into the profile folder itself. It turns on `toolkit.legacyUserProfileCustomizations.stylesheets`, which Firefox needs before it will load `userChrome.css`.
4. Restart Firefox.

## Settings

Change these CSS variables in `userChrome.css`:

| Variable | Default | What it does |
|---|---|---|
| `--uc-glass-tint` | `57%` | How solid the floating bars are (0% = clear, 100% = solid) |
| `--uc-glass-noise` | `0.1` | Grain on the glass (0 = off) |
| `--uc-active-bg` | bar color + 35% black | Color of the active address bar and its dropdown |
| `--uc-dropdown-padding` | `8px` | Inner spacing of the address-bar dropdown |
| `--uc-ripple-x` / `--uc-ripple-color` | `22%` / dark | Where the focus ripple starts and how dark it is |
| `--uc-container-bleed` | `70%` | How far a container tab's color runs down its outline |
| `--tab-min-height` | `24px` | Tab height (the bar is this + 8px) |

## Notes

- **No real blur over pages.** In Firefox 160, `backdrop-filter` in the browser UI can't see web page content, because pages render in a separate process. The frost is faked with tint and grain. The blur rule stays in the file in case Firefox ever allows it.
- **Focus ripple position.** The ripple starts from a fixed point (`--uc-ripple-x`), because CSS can't read where you clicked.
- **Firefox 160 changes this file had to handle:** `--toolbar-bgcolor` was renamed `--toolbar-background-color`, `#urlbar-background` became `.urlbar-background`, the address-bar dropdown became a self-positioning popover, `[selected="true"]` became a bare `[selected]`, `sync-off.svg` and `send-tab-20.svg` were removed, and mini windows bring their own slide-in toolbar.

## Live editing

Set `devtools.chrome.enabled` and `devtools.debugger.remote-enabled` to `true` in `about:config`, then press **Ctrl+Shift+Alt+I** to open the Browser Toolbox. Edit `userChrome.css` in its **Style Editor** tab and changes show up straight away.
