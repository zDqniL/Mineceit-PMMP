# Mineceit Software

A stable PocketMine-MP edition designed for PvP servers and compatible with **Minecraft: Bedrock Edition 26.40** (protocol 2168).

## Features

- Bedrock 26.40 network compatibility.
- Support for LevelDB worlds using world protocol version 975.
- Updated Minecraft authentication and session encryption.
- Modern Bedrock 26.40 resource-pack negotiation.
- Vanilla-style anvil mechanics, including item repair, enchantment combination, enchanted books, incompatible enchantments, rarity and level costs, renaming, prior-work penalties, and the 39-level survival limit.
- PvP profile without the swimming or crawling pose: the server continuously corrects client-side pose prediction.
- Normal movement in water is preserved.
- Empty and filled buckets can collect or place water and lava while the player is holding `Shift`.
- Corrected mappings for Sculk Sensor, Sculk Shrieker, and Sculk Vein.

## Version

```text
PocketMine-MP 5.116.21
Minecraft: Bedrock Edition 26.40
Protocol: 2168
PHP: 8.2 or newer
```

This build is published as a stable release and is not marked as a development build.

## Installation

1. Download a PHP build compatible with PocketMine-MP.
2. Place `PocketMine-MP.phar` next to `start.cmd`, `start.ps1`, or `start.sh`.
3. Start the server and accept the license when prompted.
4. Configure `server.properties`, `pocketmine.yml`, and your plugins for your PvP server.

## Building from source

Install the Composer-locked production dependencies and generate the PHAR:

```bash
composer install --no-dev --classmap-authoritative
php -dphar.readonly=0 build/server-phar.php
```

Use a PHP build containing all extensions required by PocketMine-MP. See [BUILDING.md](BUILDING.md) for additional information.

## Main fork changes

The custom changes are primarily located in:

- `src/network/mcpe/handler/InGamePacketHandler.php`: continuous suppression of swimming and crawling poses.
- `src/crafting/ItemCombineRecipe.php`: vanilla-style anvil enchantment combination and costs.
- `src/crafting/MaterialRepairRecipe.php`: material repairs and prior-work penalties.
- `src/world/World.php`: water and lava bucket usage while holding `Shift`.
- `src/data/bedrock/block/convert/VanillaBlockMappings.php`: Sculk family mappings.
- `src/block/SculkVein.php`: multi-directional block-state compatibility.

## Credits

This project is derived from:

- [PocketMine-MP](https://github.com/pmmp/PocketMine-MP), originally created and maintained by the PocketMine Team.
- [Plutonium-Mcpe/PocketMine-MP](https://github.com/Plutonium-Mcpe/PocketMine-MP), used as the compatibility base for Bedrock 26.40.
- The BedrockProtocol, BedrockData, and NBT libraries declared in `composer.lock`.
- Gemini AI for helping write the [README.md](README.md)

The original authorship history and licenses are preserved. This project is not affiliated with Mojang Studios or Microsoft.

## License

Distributed under the **GNU LGPL-3.0** license. See [LICENSE](LICENSE). If you redistribute modified binaries, you must also make the corresponding source code available and preserve all copyright and license notices.

