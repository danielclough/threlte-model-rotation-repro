<script>
    import { Canvas } from "@threlte/core";
    import Scene from "./Scene.svelte";
    import { NoToneMapping } from "three";
</script>

<div class="canvas-container">
    <Canvas
    toneMapping={NoToneMapping}
    rendererParameters={{
      powerPreference: 'low-power',
      antialias: false,
      stencil: false,
      depth: false,
      premultipliedAlpha: false
    }}>
        <Scene />
    </Canvas>
</div>

<style>
    .canvas-container {
        position: absolute;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        background: rgb(13, 19, 32);
        background: linear-gradient(
            180deg,
            rgba(13, 19, 32, 1) 0%,
            rgba(8, 12, 21, 1) 100%
        );
    }
</style>
