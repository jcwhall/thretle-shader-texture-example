<script>
  import { Canvas } from '@threlte/core';
  import Scene from '$lib/Scene.svelte';
</script>


<div class="h-screen w-full bg-gray-900">
  <Canvas>
    <Scene />
  </Canvas>
</div>

<style>
  div {
    height: 100vh;
    width: 100%;
    overflow: hidden;
  }
</style>