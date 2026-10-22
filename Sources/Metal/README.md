# Metal Implementation Notes

Start here for the 3D renderer.

- Use MetalKit MTKView.
- Command queue + render pipeline state with toon shaders.
- Uniforms for camera, model matrices, light direction.
- Ball position updated from physics each frame.

Example shader goals:
- Cel shading (dot product thresholds).
- Outline via inverted hull or post-process.
- Soft highlights for the ball.

Physics lives in CPU or compute shader for MVP (CPU is fine).
