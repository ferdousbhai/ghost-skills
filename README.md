# Ghost skills

Portable skills for Ghost and local coding agents. Skills teach the harness to
use installed CLIs through Bash/shell; they add no daemon tools or MCP servers.

## Skills

- [wacli](wacli/SKILL.md): read/search WhatsApp history, sync, and send requested
  messages using the official wacli CLI. Adapted from OpenClaw; attribution and
  the upstream revision are in the skill, with its MIT license alongside it.

## Install

Install the required CLI separately. Clone this repository and link only the
skills you want into the harness's discovery directory:

```sh
git clone https://github.com/ferdousbhai/ghost-skills.git
cd ghost-skills
mkdir -p ~/.agents/skills
ln -s "$PWD/wacli" ~/.agents/skills/wacli
mkdir -p ~/.claude/skills
ln -s ../../.agents/skills/wacli ~/.claude/skills/wacli
```

If either link path already exists, inspect it first. Keep a working discovery
link; move an older copied skill aside before replacing it. These commands do
not overwrite existing paths. Keep the clone in place while using the links.
Start a fresh agent session to discover the skill. Other harnesses may use a
different machine skill directory.

For one Ghost persona instead, link the skill to
`~/ghosts/<name>/skills/wacli`; Ghost exposes that directory as project skills
to its harnesses. The source checkout alone is not automatically discovered.

## Update or remove

Review upstream changes, then run `git pull --ff-only` in this clone to refresh
linked skills. To uninstall, remove only the discovery symlinks you created;
this leaves CLI installations, authentication, and message archives untouched.

## Scope and attribution

Keep skills small and driven by actual product needs. Provider integrations
belong to the unified service CLIs we maintain, rather than separate
Google-only or Apple-only workflows. This repository currently contains only
wacli; it does not install or configure any service integration.

Each adapted skill retains its source attribution and license. The wacli
adaptation is MIT-licensed under [wacli/LICENSE](wacli/LICENSE).
