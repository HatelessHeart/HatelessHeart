# 🎮 Getting Started - Your First Minecraft Mod!

Congratulations! You now have a complete, working Minecraft mod with a custom block model.

## 📦 What You Got

This repository now contains:

1. **A Working Minecraft Mod** - Ready to build and play!
2. **Custom Block** - "Example Block" with a purple-blue gradient texture
3. **Complete Documentation** - Everything you need to understand and customize

## 🚀 Quick Start (3 Steps!)

### Step 1: Build the Mod
```bash
# Make sure you have Java 17 installed
java -version

# Build the mod (requires Gradle installed)
gradle build

# Or if Gradle is not installed, it will use system gradle
./gradlew build
```

### Step 2: Find Your Mod
The compiled mod file will be here:
```
build/libs/examplemod-1.0.0.jar
```

### Step 3: Install & Play
1. Install Minecraft Forge 1.19.2 if you haven't already
2. Copy `examplemod-1.0.0.jar` to your Minecraft `mods` folder
3. Launch Minecraft with the Forge profile
4. Open creative mode and find "Example Block" in your inventory!

## 📚 Learning Resources

### Start Here
1. **MODEL_SYSTEM_GUIDE.md** - Visual explanation of how models work
2. **MOD_README.md** - Complete mod documentation
3. **IMPLEMENTATION_SUMMARY.md** - Technical details

### Project Structure
```
HatelessHeart/
├── src/main/
│   ├── java/                          # Java source code
│   │   └── com/hatelessheart/examplemod/
│   │       └── ExampleMod.java       # Main mod class
│   └── resources/                     # Game resources
│       ├── META-INF/
│       │   └── mods.toml             # Mod metadata
│       └── assets/examplemod/
│           ├── blockstates/          # Block state definitions
│           ├── models/               # 3D model definitions
│           ├── textures/             # PNG textures
│           └── lang/                 # Translations
├── build.gradle                       # Build configuration
└── *.md                               # Documentation files
```

## 🎨 Customization Ideas

### Change the Texture
1. Edit or replace: `src/main/resources/assets/examplemod/textures/block/example_block.png`
2. Must be 16x16 pixels, PNG format
3. Rebuild and test!

### Add More Blocks
1. Copy the block registration pattern in `ExampleMod.java`
2. Create new model files following the same structure
3. Add new textures

### Change Block Properties
In `ExampleMod.java`, modify:
```java
.strength(3.0F, 6.0F)  // hardness, blast resistance
```

Try different values:
- Stone: `strength(1.5F, 6.0F)`
- Wood: `strength(2.0F, 3.0F)`
- Diamond: `strength(5.0F, 6.0F)`

## 🔍 Understanding the Model System

### The Magic Triangle

```
Blockstate → Block Model → Texture
     ↓            ↓            ↓
  Which       What          How it
  model?      shape?        looks?
```

1. **Blockstate** (`blockstates/example_block.json`)
   - Points to which model to use
   
2. **Block Model** (`models/block/example_block.json`)
   - Defines the 3D shape (we use `cube_all`)
   - Points to texture locations
   
3. **Texture** (`textures/block/example_block.png`)
   - The actual visual appearance (16x16 PNG)

For inventory, there's also:

4. **Item Model** (`models/item/example_block.json`)
   - Usually just inherits from the block model

See **MODEL_SYSTEM_GUIDE.md** for visual diagrams!

## 🛠️ Development Tips

### Test Changes Quickly
```bash
gradle runClient  # Launches Minecraft with your mod
```

### Check for Errors
Watch the console output when running Minecraft. It will show:
- ✅ Successful block registration
- ❌ Missing textures or models
- ⚠️ Warnings about issues

### Common Issues

**"Missing texture" - Purple/black checkerboard**
- Check texture file exists
- Verify texture path in model JSON
- Ensure filename matches exactly (case-sensitive!)

**Block doesn't appear in game**
- Check console for registration errors
- Verify `BLOCKS.register(modEventBus)` is called
- Ensure block item is also registered

**Build fails**
- Verify Java 17 is installed: `java -version`
- Check Gradle version compatibility
- Read error messages carefully

## 🎯 Next Learning Steps

1. **Add a second block** - Practice the pattern
2. **Try different model parents**:
   - `cube_bottom_top` - Different top/bottom
   - `cube_column` - Column-like blocks
   - `cross` - Plant-like X shapes
3. **Add block variants** - Different textures based on state
4. **Create custom shapes** - Design your own model JSON

## 🤝 Getting Help

- Discord: hatelessheart
- Check [Forge Forums](https://forums.minecraftforge.net/)
- [Forge Documentation](https://docs.minecraftforge.net/)
- [Minecraft Wiki - Models](https://minecraft.wiki/w/Model)

## 📝 What You Learned

By building this mod, you now understand:
- ✅ Minecraft mod project structure
- ✅ How the model system works (blockstate → model → texture)
- ✅ How to register blocks with Forge
- ✅ JSON model file format
- ✅ Building and testing mods

**You're now ready to create your own Minecraft mods!** 🎉

---

## 🔗 Quick Reference

| File | Purpose |
|------|---------|
| `ExampleMod.java` | Main mod class, registers blocks |
| `mods.toml` | Mod metadata (name, version, etc.) |
| `blockstates/*.json` | Define which model to use |
| `models/block/*.json` | Define block shape and textures |
| `models/item/*.json` | Define item appearance |
| `textures/block/*.png` | Visual textures (16x16 PNG) |
| `lang/*.json` | Translations |

---

**Happy Modding!** 🎮✨
