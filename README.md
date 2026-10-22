# MagicGolfDuo

**Dusty's Magic iPhone Duo Laptop-Mode Mini-Golf**

Cute whimsy chibi / Teen Titans Go-style 3D mini-golf that turns the iPhone Duo into a tabletop arcade cabinet.

## Vision
Laptop pose (~90° hinge): **top half = live 3D course + ball**, **bottom half = swing controls + power meter**.

Pure Metal for the real 3D feel, custom shaders for the chibi look, and satisfying physics.

## Art Style
- Cute chibi characters (optional caddie / ball mascot)
- Bold outlines, exaggerated proportions, flat-to-soft shading
- Teen Titans Go energy: bright colors, simple shapes, playful expressions
- Liquid-glass accents matching Dusty's Magic brand

## MVP Scope
1. Single hole (simple putting green + one obstacle)
2. Laptop-mode split layout (ArrangementView / size classes + reserved regions)
3. Metal-rendered 3D scene
4. Basic physics (projectile + bounce + friction)
5. Touch controls on bottom half
6. Score / strokes tracking
7. Hinge-aware juice (subtle camera or power feel via onHingeChange)

## How It Works (Laptop Mode)
- Detect hinge status / angle with `onHingeChange`.
- When partially open (~laptop pose), layout:
  - Top region: MTKView / Metal view showing 3D course.
  - Bottom region: UI controls (swing meter, power slider, club selector, putt button).
- Avoid the crease with ReservedRegion.

## Metal Architecture
- **Renderer**: Custom Metal renderer (or RealityKit + Metal custom materials).
- Scene graph: course mesh, ball (sphere with custom shader), hole, simple props.
- Camera: fixed elevated view on top half that tracks the ball.
- Shaders:
  - Chibi outline + cel-shading / toon lighting.
  - Soft specular for liquid-glass ball.
  - Simple shadow map or blob shadows.
- Frame loop: update physics → update transforms → encode Metal commands.

## Physics
- Ball as rigid body (or custom Verlet / simple Euler integration).
- Gravity, drag, rolling friction.
- Collision with ground plane, simple meshes (AABB or sphere-vs-mesh for MVP).
- Bounce restitution ~0.3–0.6 for putts.
- Power from swing meter maps to initial velocity.
- Optional: hinge angle slightly modulates loft or camera tilt for feel.

## Controls (Bottom Half)
- Big swing meter (tap to start, tap again to set power).
- Direction via drag or tilt (device motion optional).
- Put button / release.
- Club select (putter for MVP).
- Restart hole / next hole.

## Project Structure (Suggested)
```
MagicGolfDuo/
├── Sources/
│   ├── App/
│   ├── Metal/
│   │   ├── Renderer.swift
│   │   ├── Shaders.metal
│   │   └── Scene.swift
│   ├── Physics/
│   └── UI/
├── Assets/
└── Docs/
```

## Next Steps
- Xcode 27.1 project targeting iOS 27.1
- Device Hub testing of laptop pose
- Simple Metal triangle → scene → ball
- Integrate physics loop
- Chibi asset placeholders (USDZ or custom meshes)

Built for Dusty's Magic — magic on the fold.
