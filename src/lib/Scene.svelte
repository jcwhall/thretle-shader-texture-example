<script>
// @ts-nocheck

  import { T, useTask } from '@threlte/core';
  import { useTexture } from '@threlte/extras';

  import vertexShader from '$lib/shaders/vertex.glsl?raw'
  import fragmentShader from '$lib/shaders/fragment.glsl?raw'

  // 1. Load the texture (This is an example texture from Threejs)
  const texture = useTexture('uv_grid_opengl.jpg');


  // 2. Uniforms Setup
  let uniforms = {
    uTime: { value: 0 },
    uTexture: { value: null }
  };

  // 3. Animation Loop
  let time = 0;
  useTask((delta) => {
    time += delta;
    uniforms.uTime.value = time;
  });

  // 4. Update texture uniform when it loads
  $: if ($texture) {
    uniforms.uTexture.value = $texture;
  }
</script>

{#if $texture}
  <T.Mesh rotation={[15, 15, 0]}>
    <T.BoxGeometry args={[2, 2, 2]} />
    <T.ShaderMaterial
      {vertexShader}
      {fragmentShader}
      {uniforms}
    />
  </T.Mesh>
{/if}