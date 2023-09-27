# threlte-model-rotation-repro

<a href="https://stackblitz.com/github/danielclough/threlte-model-rotation-repro">
  <img
    alt="Open in StackBlitz"
    src="https://developer.stackblitz.com/img/open_in_stackblitz.svg"
  />
</a>

## Issue:

Panning and Rotation of the camera causes rotation of the model's parts with respect to the rest of the model.

## Changes:
 - `/src/lib/components/App.svelte`
 - `/src/lib/components/avatars/`
 - `/static/gltf/`

The models came from [Quaternius' Animated Characters Pack](https://opengameart.org/content/animated-characters-pack) and were converted from `.blend` with Blender before using `@threlte/gltf@latest` to create `.svelte` files.

🥰 Thank you again for you help, again! 🥰