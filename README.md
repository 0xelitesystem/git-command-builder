# Git Command Builder

From "I want to..." to the exact git command. A task-first git helper for people who know what they want but not the incantation. Search for the goal in plain words ("undo last commit", "delete branch", "force push"), pick the task, and get the command with every flag explained and a safety warning where it matters.

**Live demo:** https://0xelitesystem.github.io/git-command-builder/

## Use

1. Press `/` or click the search box and type what you want to do, like "undo last commit".
2. Pick the matching task.
3. Fill in the branch name, file path, or message fields; they substitute live into the command.
4. Read the flag notes and any safety warning, then copy the command.

## Why this exists

Most people know what they want git to do but not the exact incantation, and the wrong flag can lose work. This tool maps plain goals to commands with warnings and safer alternatives. It is one HTML file with inline CSS and JavaScript: no account, no tracking, no analytics, no external scripts or fonts, and it works offline. MIT licensed, so you can fork it, self-host it, or read every line.

## Features

- 41 everyday git tasks phrased as goals, grouped into 9 categories: undoing things, branches, stash, history, remotes, sync, tags, cleanup, config
- Live search that filters by goal words ("undo", "rename", "stash")
- Exact commands in copyable code blocks, with placeholders clearly marked like `<branch-name>`
- Small input fields (branch name, file path, commit message) that substitute live into the command
- Plain-language explanation of what each flag does
- Destructive commands (`reset --hard`, `clean -f`, force push, branch `-D`, tag deletion, stash drop) carry a visible warning badge plus a safer alternative, like `--force-with-lease` over `--force` and `clean -n` dry runs before `clean -f`
- Dark mode, keyboard friendly (press `/` to jump to search), single HTML file, no external dependencies, works offline

## How it works

Everything is one `index.html` with all CSS and JavaScript inline. The task catalog is a plain array in the page source: each task holds its goal, category, search keywords, command templates, flag explanations, and optional warning text. Selecting a task renders the templates, and typing into the input fields re-substitutes your values into the command in real time. The copy button writes the current command (with your values, or the `<placeholder>` markers if you left a field blank) to the clipboard.

There is no build step. Open `index.html` in any modern browser, or:

```bash
python -m http.server 8000
```

## Privacy

All client-side. Nothing you type leaves the browser: no requests, no analytics, no external scripts or fonts (system font stack only). Verify by opening DevTools and watching the network tab. The only thing written to storage is your light or dark theme choice, saved in localStorage under the key `theme`.

## Run locally

```bash
git clone https://github.com/0xelitesystem/git-command-builder
cd git-command-builder
```

Then open `index.html` in any modern browser. Or serve the folder with `python -m http.server 8000` and visit http://localhost:8000.

## Build

No build step. The whole tool is one `index.html` with no dependencies, so there is nothing to install or compile.

## Scope

Honest scope note: this covers the everyday tasks that send most people searching the web, not the full git reference. For anything exotic, `git help <command>` is the source of truth.

## More

Part of a catalog of single-file browser tools and plain-language references, all MIT licensed and dependency-free: [0xelitesystem.github.io](https://0xelitesystem.github.io/). Built by [elitesystem.ai](https://elitesystem.ai).

## License

MIT. Copyright 0xelitesystem 2026.
