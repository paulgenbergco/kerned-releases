# Changelog

Newest first. Version numbers match the DMG and the About box.

## 0.1.5 · 2026-09-18

**The first-time-user fixes.** User sent twelve numbered reports with screenshots. Five of them were one bug, and this build closes those five plus three more. Nothing new; everything that made the editor feel broken in the first minute.

- Every style bar command that adds a marker (heading, list, task, quote) now puts the caret after it, so what you type lands inside the new block instead of in front of the marker.
- A typed numbered list continues on Enter and nests on Tab the moment you type it, including right below a diagram. Enter on an empty item ends the list.
- Typing `*`, `_` or a backtick over the closing one Kerned just inserted steps past it instead of adding another pair, so `***` and `___` type through for a horizontal rule.
- The arrow keys never leave the caret on a code fence line, where typing used to break the block open. A code block at the end of a document always has a line after it to move to.
- Bullets, checkboxes and numbers now share one shade.

Same file-safety contract.

## 0.1.4 · 2026-09-08

**This release exists to prove the updater works.** 0.1.3 could update itself in testing, but only from a copy built on the machine. This is the first one that has to travel the real path: an app that came out of a DMG, sitting in Applications, replacing itself. If your 0.1.3 offered you this build and you are reading these notes in 0.1.4, it worked.

There is almost nothing else in it, on purpose.

- The Heading menu has icons now, an H sized to each level. It was the last of the three menus without them.
- Internal tidying with no visible effect: the handful of places that pull a file name or folder out of a path now share one piece of code.

Same file-safety contract.

## 0.1.3 · 2026-09-08

**Kerned can update itself.** This is the last build you have to download by hand. From here it tells you when there is a newer one and installs it for you.

- Kerned checks once a day, shortly after launch, and says nothing unless there is something newer. A version you wave away is not offered again.
- Kerned > Check for Updates… always answers, including "up to date" and any error, because you asked.
- An update shows as a small pill at the bottom of the window with the version, a link to the notes and Install. Nothing is downloaded until you press it.
- Installing swaps the app in place. Restarting is a separate step, and it asks about unsaved work first with the same prompt Quit uses. If you say no, the new version simply starts the next time you open Kerned.
- The check sends the platform, the architecture and the version you are running. Nothing else: no account, no identifier, nothing about your documents. The editor itself still cannot reach the network at all.

Apple Silicon only, which is what the download has always been.

Same file-safety contract.

## 0.1.2 · 2026-09-08

**Window chrome, and light or dark without leaving the app.** The tray now owns the left edge the way a real sidebar does, the style bar folds out of the way when you want the width back, and the appearance is finally yours to pick rather than whatever the Mac is doing.

- The tray runs the full height of the window, title bar included, with one divider between it and the document. The traffic lights sit over its header.
- A New Document button sits beside the traffic lights: in the tray's header while it is open, in the title bar when it is not, the same spot either way.
- The tray hides and comes back from View > Tray, Option+Cmd+S, or its button, and resizes by dragging its right edge. Double-click the edge to put the width back.
- The style bar collapses rather than disappearing. A tab on its right edge slides the bar out past the edge and stays behind, flush in the gutter, so the control that brings it back sits exactly where it went. The document takes back the width the bar was holding. Shift+Cmd+Y and View > Style Bar do the same thing.
- Appearance: System, Light or Dark, from the switch at the foot of the style bar or View > Appearance. It carries through the document, the window chrome and the traffic lights, and defaults to System. This is the one and only display setting.
- The list menu has icons for bullet, numbered and task lists. The separate task button is gone; it was the same command twice. The More menu has icons too.
- Tray width and visibility, the style bar's state and the appearance choice are all remembered across launches.

Same file-safety contract.

## 0.1.1 · 2026-09-04

**Fixes saving.** 0.1.0 could not save at all from the packaged app ("Could not save file: expected raw body"): the app's security policy blocked the fast IPC path and the fallback path was refused. If you have 0.1.0, replace it with this build.

Also list editing. Same file-safety contract.

- Saving works in the packaged app. Regression test added to the release routine.
- Lists: Tab nests an item under the previous one and restarts numbering at 1; Shift+Tab moves it back out. Surrounding numbers fix themselves. Previously Tab added two spaces and left the number alone.
- Lists: Enter on any line of an item starts the next item, including the wrapped lines of a long item. Shift+Enter is a line break inside the item. Previously Enter on a wrapped line only added a line break.
- Lists: a numbered item whose first line is a heading (`1. ## Title`) keeps its number at body size, the way Bear does, instead of a clipped sliver.
- Lists: wrapped lines inside an item now line up with the item's first line, and each nested level indents by the theme's list indent.
- Lists: bullets are drawn shapes that change by level (dot, ring, square) so nesting reads at a glance.

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
