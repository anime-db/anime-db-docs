# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Structure

Pure Markdown documentation repository for the Anime DB application. No build system.

```
en/          # English docs
ru/          # Russian docs (mirrors en/ exactly)
images/
  en/        # Screenshots for English docs
  ru/        # Screenshots for Russian docs
```

Both `en/` and `ru/` share the same subdirectory layout:

```
user/
  index.md                    # Table of contents
  start.md, port.md, bot.md
  install/dist/{windows,nix}.md
  install/source/{windows,nix}.md
  item/add/{manually,search,search_in_all,fill}.md
  item/{change,delete,refill,fields}.md
  storage/{list,add,change,delete,scan}.md
  general/{search,labels,notice,notice_list,plugins,update}.md
developer/
  index.md
```

## Conventions

- **Bilingual parity**: every file added or changed in `en/` must have a counterpart in `ru/`, and vice versa. The directory structure must stay identical between the two languages.
- **Links**: use absolute paths from the repo root, e.g. `/en/user/start.md`. Index files in `{lang}/user/index.md` serve as the table of contents for each language.
- **Images**: place screenshots under `images/{lang}/` matching the doc section (e.g. `images/ru/storage/scan.jpg`). Reference them with relative or root-absolute paths consistent with existing docs.
- **Header style**: use ATX headers (`#`, `##`) — not Setext underline style. Existing bot.md files use Setext; new files should use ATX.
