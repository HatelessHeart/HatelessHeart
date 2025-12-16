# Minecraft Block Model System - Visual Guide

## File Relationship Diagram

```
Game Render Engine
        |
        | "What model for example_block?"
        v
┌─────────────────────────────────────────────────────────────┐
│ blockstates/example_block.json                              │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ {                                                         │ │
│ │   "variants": {                                          │ │
│ │     "": {                                                │ │
│ │       "model": "examplemod:block/example_block" ◄────────┼─┼── Points to block model
│ │     }                                                    │ │
│ │   }                                                      │ │
│ │ }                                                        │ │
│ └─────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
        |
        | "Use this model"
        v
┌─────────────────────────────────────────────────────────────┐
│ models/block/example_block.json                             │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ {                                                         │ │
│ │   "parent": "block/cube_all", ◄──────────────────────────┼─┼── Inherits cube shape
│ │   "textures": {                                          │ │
│ │     "all": "examplemod:block/example_block" ◄────────────┼─┼── Points to texture
│ │   }                                                      │ │
│ │ }                                                        │ │
│ └─────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
        |
        | "Apply this texture"
        v
┌─────────────────────────────────────────────────────────────┐
│ textures/block/example_block.png                            │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │                                                           │ │
│ │     [16x16 Purple-Blue Gradient PNG Image]               │ │
│ │     See: https://github.com/user-attachments/            │ │
│ │          assets/aa983125-7ef5-4de6-921e-d09052ba615f     │ │
│ │                                                           │ │
│ └─────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
        |
        v
   [Rendered Block in Game]


For Inventory Display:
┌─────────────────────────────────────────────────────────────┐
│ models/item/example_block.json                              │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ {                                                         │ │
│ │   "parent": "examplemod:block/example_block" ◄───────────┼─┼── Reuses block model
│ │ }                                                        │ │
│ └─────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

## How It Works

### 1. Game Query
When Minecraft needs to render "example_block", it looks up the blockstate file.

### 2. Blockstate Response
The blockstate file says "use the model at examplemod:block/example_block"

### 3. Model Definition
The block model file:
- Inherits from "cube_all" (a built-in model that creates a cube)
- Specifies the texture path for all faces

### 4. Texture Application
The texture PNG file (16x16 pixels) is applied to all faces of the cube.

### 5. Result
A fully textured 3D block appears in the game!

## Item Model Inheritance

The item model (for inventory) simply points back to the block model:
- No need to define the shape again
- Same appearance in hand and in world
- DRY (Don't Repeat Yourself) principle

## Key Concepts

### Parent Models
- `cube_all`: Cube with same texture on all 6 sides
- `cube`: Cube with different textures per side
- `cube_column`: Cube with top/bottom different from sides
- Custom: You can define your own shape

### Texture Paths
Format: `"modid:path/to/texture"`
- `modid`: Your mod's ID (examplemod)
- `path`: Relative to `assets/modid/textures/`
- No `.png` extension in JSON files

### Blockstates
Can have variants for different states:
```json
{
  "variants": {
    "facing=north": { "model": "..." },
    "facing=south": { "model": "...", "y": 180 },
    ...
  }
}
```

Our simple block has no variants, so we use `""` (empty variant).

## Model Hierarchy

```
Vanilla Minecraft Models (built-in)
    └── block/cube_all
        └── examplemod:block/example_block (our model)
            └── examplemod:item/example_block (our item)
```

This inheritance means we only need to specify what's different!
