# Kerned

A markdown viewer and editor for macOS that edits your markdown file. Nothing else.

**[Download the latest build](https://github.com/paulgenbergco/kerned-releases/releases/latest)** · [What changed](CHANGELOG.md) · [kerned.app](https://kerned.app) · [Why it works this way](https://kerned.app/why)

This repo holds no application code. Kerned is closed source for now; what lives here are the builds and the record of what changed between them.

## The one guarantee

The file on disk is the only source of truth.

Open a file, save it without touching anything, and `git diff` shows nothing. Change one character and the diff is one character. No normalising, no reflowing, no helpful cleanup of your line endings. A file with CRLF endings keeps them. A file with no trailing newline still has none. A byte-order mark survives. An over-escaped RSS import comes back exactly as ugly as it went in.

That is not a feature, it is the thing the app is for. Every markdown file worth caring about already lives somewhere: in a git repo, in a folder that syncs, next to code, or being written and re-read all day by an agent. An editor that reformats to its own taste is not an editor, it is an importer.

The guarantee is held up by test rather than by intention. Every fixture is opened, saved untouched and compared byte for byte, and the fixtures are chosen to be hostile: CRLF, no trailing newline, a BOM, emoji, right-to-left text, a table with ragged padding, a nested list with mixed indentation.

## How it is built

| | |
|---|---|
| Shell | Tauri 2 (Rust) |
| Interface | React 19, TypeScript, Vite |
| Editor | CodeMirror 6 via `@atomic-editor/editor` |
| Diagrams | Mermaid, rendered as block widgets |
| Platform | macOS 13 or later, Apple Silicon |

**CodeMirror, never ProseMirror.** The document is the raw markdown text. Everything you see is view-only decoration over those bytes: headings sized, list markers drawn, tables fitted to the window, syntax faded rather than hidden so you always know you are looking at plain text. An editor whose source of truth is a document model will eventually rewrite your file to match that model. It is disqualified here whatever else it does well.

**Saves are atomic.** Write to a temporary file in the same directory, flush, rename over the original. The target is never truncated in place, so a crash mid-save leaves the original intact.

**The file is watched.** Edits from git, a script or another editor show up without reloading. If your buffer is clean it reloads silently and keeps your scroll position. If it is dirty you are asked, and nothing is merged or thrown away on your behalf.

## What it does not do

No accounts. No cloud. No database of your notes. No sync, no tags, no backlinks, no graph view, no plugins, no second brain. No preferences window with two hundred switches: how it looks was decided once, carefully.

The editor cannot reach the network at all. The content security policy names no remote origin, so nothing the document surface renders or runs can make a request. Since 0.1.3 the app asks one question of one server, which is whether a newer build of itself exists. That request carries the platform, the architecture and the version you are running. Nothing about you, nothing about your documents, no identifier, no account.

## Updates

From 0.1.3 onward Kerned updates itself. It checks about once a day, says nothing unless there is something newer, and downloads nothing until you press Install. Kerned > Check for Updates… always answers, including when there is nothing to report.

Updates are signed with a key separate from the Apple Developer ID, and an installed copy refuses anything that does not verify against the public half compiled into it. Restarting is a step of its own and asks about unsaved work first.

Every release is also a DMG, signed and notarized, so a manual download stays the fallback.

## Install

Open the DMG and drag Kerned to Applications. Apple Silicon, macOS 13 or later.

## Feedback

It is alpha, and the interesting reports are the ones about how it feels to read and write in. [kerned.app#feedback](https://kerned.app#feedback), or open an issue here.
