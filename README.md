# ai-loadout

Harness-neutral AI config, kept in one place. It holds skills now and will hold more later.

## Setup

Clone the repo to `~/.agents`. Skills live in `skills/`.

### Claude Code

Link each skill into the Claude Code skills folder. If an old folder with the same name is already there, remove it first. This is a manual step for each skill:

```
ln -s ../../.agents/skills/<name> ~/.claude/skills/<name>
```

### Codex CLI

Not tested yet, because Codex is not installed on the machine this was set up on. A link from the Codex skills folder is expected to work the same way, but this is unverified.

## Skills

- `grill-me`: A relentless interview to sharpen a plan or design, asked through the AskUserQuestion tool.
- `unslop`: Cut AI tells from any writing. Must always apply.

## Credits

Both skills are adapted from upstream versions and edited here.

- `grill-me` is adapted from [grill-me](https://github.com/mattpocock/skills/tree/main/skills/productivity/grill-me) in [mattpocock/skills](https://github.com/mattpocock/skills) by Matt Pocock.
- `unslop` is adapted from [unslop](https://github.com/cursor/plugins/tree/main/pstack/skills/unslop) in [pstack](https://github.com/cursor/plugins/tree/main/pstack) (part of cursor/plugins) by Lauren Tan.

## Notice

The upstream works above are MIT licensed. Their copyright notices:

- Copyright (c) 2026 Matt Pocock (mattpocock/skills)
- Copyright (c) 2026 Lauren Tan (pstack)

## License

MIT. See `LICENSE`.
