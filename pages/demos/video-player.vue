<script setup lang="ts">
async function loadSystems() {
  //@ts-ignore
  await import('aframe-sun-sky');
}
</script>

<template>
  <AFrameScene :load-systems="loadSystems">
    <a-sun-sky material="sunPosition: -0.2 4 -5"></a-sun-sky>
    <a-assets>
      <video
        id="drone-video"
        preload="auto"
        loop="true"
        width="160"
        height="90"
        :src="usePublic('assets/videos/lambertville-drone.mp4')"
        crossorigin="anonymous"
        title="This is a Title"
      ></video>
      <video
        id="drone-video2"
        preload="auto"
        loop="true"
        width="160"
        height="90"
        :src="usePublic('assets/videos/lambertville-drone.mp4')"
        crossorigin="anonymous"
        title="This is a Title"
        description="This is a description. This is a description. This is a description. This is a description. This is a description."
      ></video>
      <video
        id="trash-video"
        preload="auto"
        loop="true"
        width="160"
        height="90"
        :src="usePublic('assets/videos/DamageAndDebrie.mp4')"
        crossorigin="anonymous"
      ></video>
    </a-assets>

    <a-playback-video
      src="#drone-video"
      position="0 0 -20"
      rotation="0 0 0"
    ></a-playback-video>
    <a-playback-video
      src="#drone-video2"
      position="20 3 -20"
      rotation="0 -35 0"
      width="32"
    ></a-playback-video>
    <a-playback-video
      src="#trash-video"
      position="0 1.6 -5"
      rotation="0 180 0"
    ></a-playback-video>
    <a-entity
      camera
      look-controls="pointerLockEnabled: true"
      wasd-controls
      position="0 1.6 0"
    >
      <a-animated-cursor></a-animated-cursor>
    </a-entity>
  </AFrameScene>
</template>
