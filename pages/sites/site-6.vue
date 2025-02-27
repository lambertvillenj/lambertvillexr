<script setup lang="ts">
const title = 'Curley Lane';
definePageMeta({
  pageName: 'Curley Lane',
});

async function loadSystems() {
  //@ts-ignore
  await import('@/aframe/components/button');
  await import('@/aframe/components/audio-player');
  await import('@/aframe/components/slide-show');
  await import('@/aframe/components/text-box');
  await import('@/aframe/components/material-override');
  await import('@/aframe/components/music-radio');
  await import('@/aframe/components/three-layer');
}
</script>

<template>
  <AFrameScene
    :load-systems="loadSystems"
    :start-title="title"
    start-description="If you're at the site, please press the start button while facing the site marker. Otherwise, just press the start button."
  >
    <a-assets>
      <img id="pano" :src="usePublic('assets/sites/site6/pano.jpg')" />
      <audio
        id="interview"
        :src="usePublic('assets/sites/site6/interview6.mp3')"
        preload="auto"
        title="Rosso Family Interview"
        description="Listen to the audio clip to hear an interview with the Rosso Family."
      ></audio>
      <a-asset-item
        id="Person1"
        :src="usePublic('assets/sites/site6/Person1.glb')"
      ></a-asset-item>
      <a-asset-item
        id="Person2"
        :src="usePublic('assets/sites/site6/Person2.glb')"
      ></a-asset-item>
      <a-asset-item
        id="Person3"
        :src="usePublic('assets/sites/site6/Person3.glb')"
      ></a-asset-item>
      <a-asset-item
        id="Person4"
        :src="usePublic('assets/sites/site6/Person4.glb')"
      ></a-asset-item>
      <a-asset-item
        id="Person5"
        :src="usePublic('assets/sites/site6/Person5.glb')"
      ></a-asset-item>
      <a-asset-item
        id="Person6"
        :src="usePublic('assets/sites/site6/Person6.glb')"
      ></a-asset-item>
      <!-- Rendering Slide Show -->
      <img
        class="render-slide-show"
        :src="usePublic('assets/sites/site6/renders/slide1.png')"
        description="Curley Lane site after the two houses were destroyed by flooding."
      />
      <img
        class="render-slide-show"
        :src="usePublic('assets/sites/site6/renders/slide2.png')"
        description="Curley Lane site reimagined as a naturalized park."
      />
      <img
        class="render-slide-show"
        :src="usePublic('assets/sites/site6/renders/slide3.png')"
        description="Curley Lane site reimagined with native plantings."
      />
      <!-- Photo Slide Show -->
      <img
        class="photo-slide-show"
        :src="usePublic('assets/sites/site6/photos/slide4.jpg')"
        description="Floodwaters resulting from Hurricane Ida."
      />
      <img
        class="photo-slide-show"
        :src="usePublic('assets/sites/site6/photos/slide5.jpg')"
        description="Viewing an ongoing flood from inside."
      />
      <img
        class="photo-slide-show"
        :src="usePublic('assets/sites/site6/photos/slide7.jpg')"
        description="The Rosso family bought the home in 1920 and held it for 103 years until Hurricane Ida washed it away."
      />
      <img
        class="photo-slide-show"
        :src="usePublic('assets/sites/site6/photos/slide8.jpg')"
        description="Two houses at Curley Lane collapsed after flooding caused by Hurricane Ida."
      />
      <audio
        class="music"
        :src="usePublic('assets/music/end-poem-smooth.wav')"
      ></audio>
      <audio
        class="music"
        :src="usePublic('assets/music/iron-golem-vibe.wav')"
      ></audio>
      <audio class="music" :src="usePublic('assets/music/new-me.wav')"></audio>
    </a-assets>

    <a-sky
      src="#pano"
      three-layer="desktopLayers: 1"
      rotation="11.7 90 0"
    ></a-sky>
    <a-music-radio></a-music-radio>

    <!-- Content -->
    <a-entity rotation="0 10 0" position="0 1 0" three-layer="layers: 1">
      <!-- People -->
      <a-entity rotation="0 -50 0">
        <a-entity
          material-override="color: black"
          three-layer="layers: 1"
          position="-50 0 -20"
        >
          <a-gltf-model src="#Person1" position="20 -12 0"></a-gltf-model>
          <a-gltf-model src="#Person2" position="14 -6 -55"></a-gltf-model>
          <a-gltf-model src="#Person3" position="34 -9 -25"></a-gltf-model>
          <a-gltf-model src="#Person4" position="-4 -8 -35"></a-gltf-model>
          <a-gltf-model src="#Person5" position="12 -5 -45"></a-gltf-model>
          <a-gltf-model src="#Person6" position="3 -7 -65"></a-gltf-model>
        </a-entity>
      </a-entity>
      <!-- Interview Audio -->
      <a-entity rotation="0 -100 0">
        <a-audio-player
          src="#interview"
          position="0 0 -6"
          title="Interview"
          description-width="2.2"
        ></a-audio-player>
      </a-entity>
      <!-- Text Box -->
      <a-entity rotation="0 40 0">
        <a-text-box
          width="3"
          height="3"
          position="0 1.5 -6"
          :title="title"
          description="Interact with the slides and audio to learn about the devastation caused by flooding at Curley Lane Blue Acres."
        ></a-text-box>
      </a-entity>
      <a-entity rotation="0 40 0">
        <a-text-box
          position="-1 -1 -6"
          width="5"
          height="3"
          title="Swan Creek Flooding"
          description="Although not located in a designated flood zone, the homes at 2 Curley Lane and 4 Curley Lane were destroyed by the flooding of Swan Creek during Hurricane Ida and have since been removed.\n\nSpecific plans for this site have not yet been made, though one idea includes a naturalized park where visitors can enjoy the creek and sylvan views."
        ></a-text-box>
        <a-entity rotation="0 80 0">
          <!-- Photo Slide Show -->
          <a-slide-show
            position="0 4 -6"
            rotation="10 0 0"
            image-query=".photo-slide-show"
            autoplay="true"
            autoplay-duration="5000"
            description-height="3"
          ></a-slide-show>
          <!-- Render Slide Show -->
          <a-slide-show
            rotation="-10 0 0"
            position="0 -2 -6"
            image-query=".render-slide-show"
            autoplay="true"
            autoplay-duration="5000"
            description-height="3"
          ></a-slide-show>
        </a-entity>
      </a-entity>
    </a-entity>
    <a-entity
      camera
      look-controls="pointerLockEnabled: true"
      wasd-controls="enabled:false"
      position="0 1.6 0"
      three-layer="layers: 1"
    >
      <a-animated-cursor></a-animated-cursor>
    </a-entity>
  </AFrameScene>
</template>
