---
name: omdrop-install
description: Install Omdrop (AirDrop for Omarchy) when the owner wants AirDrop and the `omdrop` command is missing. Install only; once installed, Omdrop's own bundled `omdrop` skill covers usage.
---

# Install Omdrop

Omdrop (`omdrop`, Omarchy plugin `netmojo.omdrop`; not "omadrop") sends and
receives AirDrop files and links with nearby Apple devices. This skill only
installs it. Usage instructions ship with the plugin as its own `omdrop` skill,
which the plugin installs and keeps current.

Run everything through the harness's Bash/shell tool.

1. **Already installed?** Check `command -v omdrop` or
   `~/.config/omarchy/plugins/netmojo.omdrop/bin/omdrop`. If present, stop
   here and follow the `omdrop` skill (start a fresh session if it is not yet
   loaded).
2. **Supported hardware?** Omdrop targets Apple Silicon Macs running Omarchy
   with supported Broadcom Wi-Fi/AWDL firmware, not arbitrary Linux PCs.
   `aarch64` alone does not prove compatibility; check the
   [requirements](https://github.com/brentkearney/omdrop-plugin#requirements).
   On unsupported hardware, explain the limitation instead of installing.
3. **Explain, then install.** Installation adds a shell plugin, an AWDL driver,
   receiver dependencies, and a narrow firewall rule. With the owner's go-ahead:

   ```bash
   omarchy plugin add https://github.com/brentkearney/omdrop-plugin.git
   ~/.config/omarchy/plugins/netmojo.omdrop/bin/omdrop setup
   ```

   The owner enables the plugin when prompted. `setup` puts `omdrop` on PATH
   and links the bundled `omdrop` skill into the agent skill directories.
4. **Driver.** If `omdrop doctor` reports a missing or outdated driver, have the
   owner run `omdrop install-driver` in a terminal they can watch; the product
   handles privilege elevation.
5. **Start a fresh agent session** so the `omdrop` skill is discovered.

Never collect the owner's password, load arbitrary driver builds, or change the
firewall by hand. Installing does not authorize sending files or making this
computer discoverable.
