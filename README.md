# Ghost skills

An index of the products Ghost recommends, not a copy of their skills. Each
product ships and maintains its own agent skill in its repository; this repo
only tells an agent which product covers a task and how to install that skill.
Skills that no product ships may be added here to fill a gap.

## Skills

| Skill | Purpose |
| --- | --- |
| [ghost-products](ghost-products/SKILL.md) | Index: mail, calendars, contacts, tasks, iCloud apps, file sync, Drive/Docs/Sheets, WhatsApp, AirDrop; installs each product's own skill and covers the gaps (Omdrop install, wacli on Linux, gws scoping) |

## Where product skills live

| Product | Skill source |
| --- | --- |
| Cloudmail | [cloud-mail/skills/cloudmail](https://github.com/ferdousbhai/cloud-mail/tree/main/skills/cloudmail) (also built into `cloudmail skill`) |
| Cloud Calendar | [cloud-calendar/skills/cloud-calendar](https://github.com/ferdousbhai/cloud-calendar/tree/main/skills/cloud-calendar) |
| Cloud Contacts | [cloud-contacts/skills/cloud-contacts](https://github.com/ferdousbhai/cloud-contacts/tree/main/skills/cloud-contacts) |
| Cloud Tasks | [cloud-tasks/skills/cloud-tasks](https://github.com/ferdousbhai/cloud-tasks/tree/main/skills/cloud-tasks) |
| iCloud for Omarchy | [icloud-for-omarchy/docs/skills/icloud](https://github.com/ferdousbhai/icloud-for-omarchy/tree/main/docs/skills/icloud) |
| Omacloud | [omacloud/skills/omacloud](https://github.com/ferdousbhai/omacloud/tree/master/skills/omacloud) |
| gws (third party) | [googleworkspace/cli/skills](https://github.com/googleworkspace/cli/tree/main/skills) |
| wacli (third party) | [OpenClaw's wacli skill](https://github.com/openclaw/openclaw/tree/main/extensions/whatsapp/skills/wacli) |
| Omdrop (third party) | bundled with the plugin; `omdrop setup` links it |

## Install

```sh
npx skills add ferdousbhai/ghost-skills -g
```

The agent then installs product skills as needed (`npx skills add <source> -g`).
To install them all up front, run the commands in the index's table yourself.

For one Ghost persona instead, link the skill under `~/ghosts/<name>/skills/`;
Ghost exposes that directory as project skills. Start a fresh agent session
after installing. `npx skills update` refreshes installed skills.

## Maintain

Fix a product's skill in that product's repository, never by copying it here.
When a product starts shipping a skill that covers a gap here, remove the gap.
