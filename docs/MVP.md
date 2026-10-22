# MagicGolfDuo MVP Details

## Core Loop
1. Place Duo in laptop pose.
2. Aim on bottom controls.
3. Swing (power meter).
4. Watch ball on top 3D view.
5. Ball settles → stroke count updates.
6. Sink the putt → celebrate (chibi particles).

## Metal Requirements
- MTKView for continuous rendering.
- Custom vertex/fragment shaders for toon + outline.
- Instanced or simple draw calls for props.
- Depth testing + basic lighting.

## Physics Sketch
```
velocity += gravity * dt
position += velocity * dt
apply friction on ground contact
resolve collisions
```

## Controls Mapping
- Bottom half exclusive for input so thumbs never cover the course.
- Large touch targets.
- Haptics on impact and hole-in.

## Art Pipeline
- Chibi models: simple low-poly with exaggerated heads.
- Textures: flat colors + outline in shader.
- Reference: Teen Titans Go, modern chibi mobile games.
