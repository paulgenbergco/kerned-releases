# Changelog

Newest first. Version numbers match the DMG and the About box.

## Unreleased

- Lists: Tab nests an item under the previous one and restarts numbering at 1; Shift+Tab moves it back out. Surrounding numbers fix themselves. Previously Tab added two spaces and left the number alone.
- Lists: Enter on any line of an item starts the next item, including the wrapped lines of a long item. Shift+Enter is a line break inside the item. Previously Enter on a wrapped line only added a line break.
- Lists: a numbered item whose first line is a heading (`1. ## Title`) shows its number at the heading's size instead of a clipped sliver.

## 0.1.0 · 2026-09-03

First build to leave the machine. Tester release.

- Opens `.md` files and writes back exactly the bytes you changed. Save without editing and `git diff` shows nothing.
- Renders headings, lists, task checkboxes, tables, code and Mermaid diagrams in place while you type. Markdown markers fade rather than disappear; the source is under the caret.
- Tables fit the window instead of scrolling sideways. Hover a table for add-column and add-row; drag to reorder.
- Several documents in one window with a tray on the left, unsaved-changes dot, Cmd+Shift+] and [ to switch. Open Recent, drag and drop, and double-click from Finder.
- Local images display. Links open in the browser; links to other `.md` files open in the tray.
- Watches the file on disk, so edits from git, scripts or another editor show up without reloading.
- Vertical style bar on the left with headings, lists, emphasis, links, tables and images. Reading mode.
- Paper theme, light and dark. Fonts and rhythm are shared between the two; only colors differ.
- Signed and notarized. No accounts, no cloud, no network.

Known rough edges: this is a first build. Tell us what broke at https://kerned.app#feedback.
