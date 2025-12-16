# Example Minecraft Mod

A simple Minecraft Forge mod demonstrating how to create a custom block with a model.

## About Me
- 👋 Hi, I'm @HatelessHeart
- 👀 I'm interested in ... Minecraft mods 
- 🌱 I'm currently learning ... How to mod minecraft
- 💞️ I'm looking to collaborate on ... How to port mods to other versions and create new minecraft mods
- 📫 How to reach me ... here or discord : "hatelessheart"

## Project Structure

This mod includes:
- **Custom Block**: A simple example block that can be placed in the game
- **Block Model**: JSON model files that define how the block looks
- **Texture Support**: Structure for adding custom textures

## File Structure

```
src/main/
├── java/com/hatelessheart/examplemod/
│   └── ExampleMod.java                    # Main mod class
└── resources/
    ├── META-INF/
    │   └── mods.toml                      # Mod metadata
    └── assets/examplemod/
        ├── blockstates/
        │   └── example_block.json         # Block state definition
        ├── models/
        │   ├── block/
        │   │   └── example_block.json     # 3D block model
        │   └── item/
        │       └── example_block.json     # Item model (in inventory)
        ├── textures/block/
        │   └── TEXTURE_README.md          # Instructions for adding textures
        └── lang/
            └── en_us.json                 # English translations
```

## Understanding the Model System

### 1. Blockstate (blockstates/example_block.json)
Defines which model to use for the block in different states. Our simple block has only one state.

### 2. Block Model (models/block/example_block.json)
Defines the 3D shape of the block. We use `cube_all` which creates a cube with the same texture on all sides.

### 3. Item Model (models/item/example_block.json)
Defines how the block looks in your inventory. It references the block model.

### 4. Texture
A 16x16 PNG image that gets applied to the block's surfaces. See `textures/block/TEXTURE_README.md` for details.

## Prerequisites

- Java 17 or higher
- Minecraft 1.19.2
- Forge 43.1.1 or higher

## Building the Mod

1. **Clone or download the repository**:
   ```bash
   git clone https://github.com/HatelessHeart/HatelessHeart.git
   cd HatelessHeart
   ```
   Or download and extract the repository files to a directory.

2. **Add a texture** (optional):
   Create a 16x16 PNG file and save it as:
   ```
   src/main/resources/assets/examplemod/textures/block/example_block.png
   ```

3. **Build the mod**:
   
   If you have Gradle installed:
   ```bash
   gradle build
   ```
   
   Or use the included wrapper (requires system Gradle):
   ```bash
   ./gradlew build
   ```
   
   On Windows:
   ```bash
   gradlew.bat build
   ```

4. **Find your mod**:
   The compiled mod will be in `build/libs/examplemod-1.0.0.jar`

## Installing the Mod

1. Install Minecraft Forge 1.19.2
2. Copy the jar file from `build/libs/` to your Minecraft `mods` folder
3. Launch Minecraft with the Forge profile
4. The block will be available in the creative inventory

## Testing in Development

To test the mod in a development environment (requires Gradle):

```bash
gradle runClient
```

Or with the wrapper:
```bash
./gradlew runClient
```

This will launch Minecraft with your mod loaded.

## Customizing the Mod

### Change the Block Name
Edit `src/main/resources/assets/examplemod/lang/en_us.json`:
```json
{
  "block.examplemod.example_block": "Your Custom Name"
}
```

### Change Block Properties
Edit `ExampleMod.java` and modify the block properties:
```java
.strength(3.0F, 6.0F)  // First number: hardness, Second: blast resistance
```

### Add More Blocks
Follow the pattern in `ExampleMod.java`:
1. Register a new block
2. Register its item form
3. Create corresponding model files in `assets/examplemod/`

## Learning Resources

- [Forge Documentation](https://docs.minecraftforge.net/)
- [Forge Community Wiki](https://forge.gemwire.uk/wiki/Main_Page)
- [Minecraft Wiki - Model Files](https://minecraft.wiki/w/Model)

## License

MIT

---

<!---
HatelessHeart/HatelessHeart is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
--->
