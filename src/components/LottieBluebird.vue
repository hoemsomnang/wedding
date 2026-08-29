<template>
  <div
    ref="lottieContainer"
    class="lottie-bird-wrapper"
    :class="{ 'flip-forward': flipForward }"
  ></div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import lottie from 'lottie-web'
import birdAnimationData from '../assets/wedding_bluebird_lottie.json'

const props = defineProps({
  speed: {
    type: Number,
    default: 1.0
  },
  flipForward: {
    type: Boolean,
    default: true
  }
})

const lottieContainer = ref(null)
let animInstance = null

onMounted(() => {
  if (lottieContainer.value) {
    animInstance = lottie.loadAnimation({
      container: lottieContainer.value,
      renderer: 'svg', // Scalable Vector Graphics (SVG)
      loop: true,
      autoplay: true,
      animationData: birdAnimationData
    })
    animInstance.setSpeed(props.speed)
  }
})

onUnmounted(() => {
  if (animInstance) {
    animInstance.destroy()
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
}

.lottie-bird-wrapper :deep(svg) {
  width: 100%;
  height: 100%;
  overflow: visible;
  filter: drop-shadow(0 4px 10px rgba(10, 35, 80, 0.4));
}

/* Flip container horizontally so the bird's head and beak point forward into the flight direction */
.lottie-bird-wrapper.flip-forward {
  transform: scaleX(-1);
  transform-origin: center center;
}
</style>
