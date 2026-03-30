# Mystery Fun House

Roblox place managed with [Rojo](https://github.com/rojo-rbx/rojo). Tooling via [Rokit](https://github.com/rojo-rbx/rokit); packages via [Wally](https://github.com/UpliftGames/wally).

## Toolchain (Rokit)

This repo lists tools in `rokit.toml`. After `rokit install`, Rokit links binaries under `~/.rokit/bin/`. Add that directory to your `PATH` (or call tools by full path) so `wally` resolves in a normal shell:

```bash
export PATH="$HOME/.rokit/bin:$PATH"
```

From the project root:

```bash
rokit install   # install/update tools from rokit.toml
wally install   # install Wally deps into Packages/ (required after clone; Packages/ is gitignored)
```

## Rojo

Build a place file:

```bash
rojo build -o "Mystery Fun House.rbxlx"
```

Live sync into Studio:

```bash
rojo serve
```

Wally shared packages are mapped to `ReplicatedStorage.Packages`. Example:

```lua
local Packages = game:GetService("ReplicatedStorage").Packages
local Promise = require(Packages.Promise)
```

If you add `[server-dependencies]` in `wally.toml`, run `wally install`, then add a `ServerPackages` `$path` under `ServerScriptService` in `default.project.json` (see [Wally + Rojo](https://wally.run/) patterns).

## Docs

- [Rojo documentation](https://rojo.space/docs)
- [Wally manifest format](https://github.com/UpliftGames/wally#manifest-format)