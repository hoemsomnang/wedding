<template>
  <div
    class="lottie-bird-wrapper"
    :class="{ 'flip-forward': flipForward }"
    :style="{ '--bird-speed': speed }"
  >
    <object
      :data="birdSvg"
      type="image/svg+xml"
      class="bird-svg"
      aria-label="Wedding Bluebird"
    >
      <img
        :src="birdSvg"
        alt="Wedding Bluebird"
        class="bird-svg"
        draggable="false"
      />
    </object>
  </div>
</template>

<script setup>
import birdSvg from '../assets/wedding_bluebird.svg'

defineProps({
  speed: {
    type: Number,
    default: 1.0
  },
  flipForward: {
    type: Boolean,
    default: true
  }
})
</script>

<style scoped>
.lottie-bird-wrapper {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  pointer-events: none;
}

.bird-svg {
  width: 100%;
  height: 100%;
  object-fit: contain;
  pointer-events: none;
  filter: drop-shadow(0 4px 10px rgba(10, 35, 80, 0.4));
}

/* Flip container horizontally so the bird's head and beak point forward into the flight direction */
.lottie-bird-wrapper.flip-forward {
  transform: scaleX(-1);
  transform-origin: center center;
}
</style>

