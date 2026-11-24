# Patchwork

A faster Minecraft Java client.

**Download:** [patchworkclient.com](https://patchworkclient.com) or the [Releases](../../releases) page.

The client's source code is closed. This repository holds:

- **Releases**: the Windows installer and portable ZIP for each version. The launcher updates itself from patchworkclient.com; every update is signed and checked before it installs.
- **Issues**: bug reports and requests to add a mod or modpack to the launcher.
- **`catalog/mods.json`**: the list of mods the launcher offers in its Patchwork tab.

## Ask for a mod or modpack

Open an issue with **[Add my mod](../../issues/new?template=add-mod.yml)** or **[Add my modpack](../../issues/new?template=add-modpack.yml)**. We check every request by hand. We need a Modrinth or CurseForge link, the Minecraft versions and loader, and, if you're not the author, a link showing the author allows redistribution or listing.

## The catalog

Pull requests to `catalog/mods.json` are welcome. The format is in [catalog/FORMAT.md](catalog/FORMAT.md). A merged change doesn't reach players straight away: the maintainers sign the catalog and publish it to patchworkclient.com. The launcher ignores any catalog without a valid signature.

## Report a bug

Use the **[Bug report](../../issues/new?template=bug.yml)** form. Attach `latest.log` from the instance's `logs` folder if the game crashed.

## Security

Please don't report security problems in a public issue. Email **contact@patchworkclient.com** instead.
