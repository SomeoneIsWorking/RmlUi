# SDL_GPU shader artifacts

`compile_shaders.py` generates the existing SPIR-V, MSL and DXIL arrays using
SDL_shadercross. `compile_wgsl.py` translates those same SPIR-V arrays to WGSL
with the pinned Naga converter owned by shared/web-port. From this repository:

```
python Backends/RmlUi_SDL_GPU/compile_wgsl.py <web-port>/tools/shaders.py
```

The converter preserves SDL clip coordinates and separates image/sampler
bindings. Generated WGSL is committed beside the other generated formats, so
ordinary application builds need no shader translator. The renderer offers
WGSL only when the SDL headers expose `SDL_GPU_SHADERFORMAT_WGSL`; upstream SDL
builds retain their existing formats and behavior. Shader byte counts exclude
the string terminator.
