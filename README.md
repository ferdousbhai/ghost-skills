# Ghost skills

Portable Bash/shell skills for Ghost and local coding agents. They use installed
product CLIs through native harness tools, without adding daemon integrations or
MCP servers. Missing products can be installed using each skill's documented
installer; account sign-in remains with the owner.

## Skills

| Skill | Product and tasks |
| --- | --- |
| [omdrop](omdrop/SKILL.md) | AirDrop files/links on supported Apple Silicon Omarchy Macs |
| [wacli](wacli/SKILL.md) | WhatsApp history, sync, and requested sends |
| [cloud-calendar](cloud-calendar/SKILL.md) | Unified iCloud, Google, and HEY calendars and events |
| [cloudmail](cloudmail/SKILL.md) | Own-domain mail, HEY, Gmail, and iCloud Mail |
| [icloud](icloud/SKILL.md) | Apple Notes, Photos, Find My, Reminders, Contacts, and shared sign-in |
| [omacloud](omacloud/SKILL.md) | Encrypted file/settings sync, versions, and machine migration |

Calendar and mail tasks use our unified products, including for iCloud; the
`icloud` skill handles the remaining iCloud apps. Provider CLIs such as `gws`
and `hey` are dependencies managed through the product workflows, not separate
agent integrations.

## Install skills

On Linux, clone this repository and link the skills you want into the harness's
discovery directory. This installs instructions, not the product binaries:

```sh
git clone https://github.com/ferdousbhai/ghost-skills.git
cd ghost-skills
mkdir -p ~/.agents/skills ~/.claude/skills
for skill in wacli cloud-calendar cloudmail icloud omacloud omdrop; do
  ln -sT "$PWD/$skill" "$HOME/.agents/skills/$skill"
  ln -sT "../../.agents/skills/$skill" "$HOME/.claude/skills/$skill"
done
```

Choose fewer names in the loop if desired. `ln -sT` refuses existing paths;
inspect those paths first, keep working discovery links, and move older copied
skills aside before replacing them. Never overwrite an unrelated skill. Keep
the clone in place while using links. Start a fresh agent session after installing.
Other harnesses may use a different machine skill directory.

For one Ghost persona instead, link selected skill directories under
`~/ghosts/<name>/skills/`; Ghost exposes those as project skills. For example:

```sh
mkdir -p ~/ghosts/sage/skills
ln -sT "$PWD/cloud-calendar" ~/ghosts/sage/skills/cloud-calendar
```

Replace `sage` with an existing ghost. The source checkout alone is not
automatically discovered. No Ghost daemon restart is needed.

## Use and install products

Ask the ghost for the actual task: check tomorrow's calendar, find an email,
look up a contact, or inspect sync status. Each skill starts with CLI detection
and a status/help check, explains the official install path when missing, and
keeps privileged installation within the owner's authorized task. If sudo needs
a password, the owner runs it in their terminal. Installing a package does not
authorize DNS changes, account creation, file sync, device approval, or sends.

The agent should use existing sign-ins and stop for the owner's browser/Apple
sign-in when needed. Never paste passwords, OAuth callbacks, or recovery keys
into chat. See each skill for provider limitations and partial-result warnings.

## Update or remove

Review changes, then run `git pull --ff-only` in this clone to refresh linked
skills. To uninstall a skill, remove only its discovery symlinks; leave product
installations, authentication, archives, and sync state intact.

## Maintain

Keep activation descriptions precise, command examples version-aware, and skills
small. Cloudmail and iCloud adapt their product-owned skills; preserve their
upstream references and check the product CLI/docs before refreshing them.
Omdrop adapts its plugin-owned skill and retains its hardware requirements.
All commands run through Bash/shell. No provider-specific alternative should
bypass the unified mail/calendar products.

Each skill includes its MIT license. wacli is adapted from OpenClaw; its pinned
upstream revision and attribution are in [wacli/SKILL.md](wacli/SKILL.md).
