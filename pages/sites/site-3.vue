<script setup lang="ts">
const title = 'Union Street Bridge';
definePageMeta({
  pageName: 'Union Street Bridge',
});

async function loadSystems() {
  //@ts-ignore
  await import('@/aframe/components/button');
  await import('@/aframe/components/audio-player');
  await import('@/aframe/components/slide-show');
  await import('@/aframe/components/click-move');
  await import('@/aframe/components/text-box');
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
      <video
        id="trash-video"
        preload="auto"
        loop="true"
        width="160"
        height="90"
        :src="usePublic('assets/sites/site3/DamageAndDebrie.mp4')"
        crossorigin="anonymous"
        description="View the cleanup efforts after Hurricane Irene."
      ></video>
      <audio
        id="interview"
        :src="usePublic('assets/sites/site3/interview3.mp3')"
        title="Hurricane Ida"
        description="Listen to this audio clip to hear stories from members of the Lambertville community about the impact of Hurricane Ida."
      ></audio>
      <img class="pano" :src="usePublic('assets/sites/site3/pano.jpg')" />
      <a-asset-item
        id="boat"
        :src="usePublic('assets/sites/site3/boat.glb')"
      ></a-asset-item>
      <a-asset-item
        id="debris"
        :src="usePublic('assets/sites/site3/debris-concrete-junk.glb')"
      >
      </a-asset-item>
      <a-asset-item
        id="slab"
        :src="usePublic('assets/sites/site4/wall.glb')"
      ></a-asset-item>
      <img
        class="slide-show"
        :src="usePublic('assets/sites/site3/slide3.jpg')"
        description="Post-Ida Damage."
      />
      <img
        class="slide-show"
        :src="usePublic('assets/sites/site3/slide5.jpg')"
        description="Post-Ida Damage."
      />
      <img
        class="slide-show"
        :src="usePublic('assets/sites/site3/slide7.jpg')"
        description="Post-Ida Damage."
      />
      <img
        class="slide-show"
        :src="usePublic('assets/sites/site3/slide8.jpg')"
        description="Post-Ida Damage."
      />
      <img
        class="slide-show"
        :src="usePublic('assets/sites/site3/slide9.jpg')"
        description="Post-Ida Damage."
      />
      <img
        class="slide-show"
        :src="usePublic('assets/sites/site3/slide10.jpg')"
        description="Post-Ida Damage."
      />
      <img
        class="slide-show"
        :src="usePublic('assets/sites/site3/slide11.jpg')"
        description="Post-Ida Damage."
      />
      <img
        class="slide-show"
        :src="usePublic('assets/sites/site3/slide14.jpg')"
        description="Post-Ida Damage."
      />
      <img id="pano" :src="usePublic('assets/sites/site3/pano.jpg')" />
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
      rotation="11.7 0 0"
      three-layer="desktopLayers: 1"
    ></a-sky>
    <a-music-radio></a-music-radio>

    <a-entity three-layer="layers: 1" rotation="0 90 0">
      <!-- Boat -->
      <a-entity id="close-boat-pos" position="-3 -2 -6" rotation="0 180 0">
      </a-entity>
      <a-entity
        rotation="0 20 0"
        position="-24 -2 -20"
        click-move="toEntity: #close-boat-pos; spinOnToEntity: true"
      >
        <a-entity position="0 0.2 0" rotation="-5 -30 -20" scale="0.5 0.5 0.5">
          <a-gltf-model src="#boat" position="0 0 -5"></a-gltf-model>
        </a-entity>
        <a-gltf-model
          src="#debris"
          position="0 -1 3"
          scale="0.1 0.1 0.1"
        ></a-gltf-model>
        <a-gltf-model
          src="#debris"
          position="-0.5 -1 -3d"
          scale="0.13 0.13 0.13"
        ></a-gltf-model>
        <a-gltf-model
          src="#slab"
          scale="0.5 0.5 0.5"
          position="2.5 -1.3 1.5"
          rotation="0 50 0"
        ></a-gltf-model>
      </a-entity>

      <!-- Content -->
      <a-entity rotation="0 -90 0" position="0 0 0">
        <a-entity rotation="0 0 0">
          <!-- Text -->
          <a-text-box
            width="3"
            height="3"
            position="0 1.3 -6"
            title="Union Street Bridge"
            description="Interact with the videos and slides to learn about the impact of flooding on the South Union Street Bridge."
          ></a-text-box>
          <!-- Interview Audio -->
          <a-audio-player
            src="#interview"
            position="-0.8 -1.4 -6"
          ></a-audio-player>
        </a-entity>
        <!-- Video -->
        <a-entity rotation="0 -60 0">
          <a-playback-video
            src="#trash-video"
            rotation="10 0 0"
            position="0 3 -6"
          ></a-playback-video>
          <!-- Slideshow -->
          <a-slide-show
            rotation="-10 0 0"
            position="0 -3 -6"
            image-query=".slide-show"
            autoplay="true"
            autoplay-duration="5000"
          ></a-slide-show>
        </a-entity>
        <!-- Boat Text -->
        <a-entity rotation="0 -160 0">
          <a-text-box
            width="4"
            height="3"
            position="0 0.75 -6"
            title="Broken Bridge"
            description="During Hurricane Irene in 2011, the upstream balustrade was destroyed when, due to the rising waters in the creek, a boat crashed over the top of the bridge and landed in the street.\n\nA virtual recreation of the boat has been made at the crash site. Click on the virtual boat to view it up close."
          >
          </a-text-box>
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
