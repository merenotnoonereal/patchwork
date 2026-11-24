# `catalog/mods.json` format

The launcher reads this file from `https://patchworkclient.com/catalog/mods.json`, together with a detached Ed25519 signature (`mods.json.sig`). A catalog without a valid signature is ignored, so a change here only reaches players once the maintainers sign and publish it.

## Top level

| Field | Rule |
|---|---|
| `schema` | exactly `1` |
| `generated` | `YYYY-MM-DDTHH:MM:SSZ` in UTC. Must be newer than the published copy, so bump it in every change. |
| `mods` | array of entries (may be empty) |

No other fields are allowed anywhere: one unknown field invalidates the whole file. The file must stay under 256 KiB.

## Entry

| Field | Required | Rule |
|---|---|---|
| `id` | yes | 2–64 chars, a lowercase letter first, then lowercase letters, digits, `_` or `-`. Unique per `game`. |
| `name` | yes | display name |
| `author` | yes | |
| `summary` | yes | one line, at most 200 chars |
| `description` | no | HTTPS project page URL |
| `icon` | no | HTTPS URL of a square PNG, 64–256 px, at most 128 KiB |
| `game` | yes | Minecraft release, e.g. `"26.3"` |
| `loader` | yes | `"fabric"` |
| `version` | yes | the mod's version, at most 64 chars |
| `updated` | no | same timestamp format as `generated` |
| `source` | yes | `{ "url": "https://..." }` |
| `sha512` | yes | 128 lowercase hex chars of the file's SHA-512 |
| `size` | yes | exact size in bytes |
| `requires` | no | ids of other catalog mods to install first |

## Where the file may live

`source.url` must be HTTPS and on `patchworkclient.com` or a GitHub release asset (`https://github.com/<owner>/<repo>/releases/download/<tag>/<file>`). Other hosts are rejected even in a signed catalog. Mods hosted only on Modrinth or CurseForge: open an **Add my mod** issue instead.

## Size and hash on Windows

```powershell
(Get-Item .\mod.jar).Length
(Get-FileHash -Algorithm SHA512 .\mod.jar).Hash.ToLower()
```

## Example entry

```json
{
  "id": "example-mod",
  "name": "Example Mod",
  "author": "someone",
  "summary": "One line about what it does.",
  "game": "26.3",
  "loader": "fabric",
  "version": "1.0.0",
  "source": { "url": "https://github.com/someone/example-mod/releases/download/v1.0.0/example-mod-1.0.0.jar" },
  "sha512": "<128 hex chars>",
  "size": 123456
}
```
