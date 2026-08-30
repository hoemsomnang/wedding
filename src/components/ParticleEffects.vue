<template>
  <div class="particles-container" aria-hidden="true">
    <!-- Floating Light Sparkles -->
    <div
      v-for="particle in sparkles"
      :key="'sparkle-' + particle.id"
      class="sparkle-particle"
      :style="{
        left: particle.x + '%',
        top: particle.y + '%',
        width: particle.size + 'px',
        height: particle.size + 'px',
        animationDuration: particle.duration + 's',
        animationDelay: particle.delay + 's',
        opacity: particle.opacity
      }"
    ></div>

    <!-- Drifting Petals -->
    <div
      v-for="petal in petals"
      :key="'petal-' + petal.id"
      class="drifting-petal"
      :class="petal.color"
      :style="{
        left: petal.x + '%',
        width: petal.size + 'px',
        height: petal.size * 1.3 + 'px',
        animationDuration: petal.duration + 's',
        animationDelay: petal.delay + 's',
        transform: `rotate(${petal.rotation}deg)`
      }"
    ></div>

    <!-- Glowing White Butterflies near bottom -->
    <div
      v-for="butterfly in butterflies"
      :key="'butterfly-' + butterfly.id"
      class="ethereal-butterfly"
      :style="{
        left: butterfly.x + '%',
        top: butterfly.y + '%',
        animationDuration: butterfly.duration + 's',
        animationDelay: butterfly.delay + 's',
        transform: `scale(${butterfly.scale})`
      }"
    >
      <svg class="butterfly-svg" viewBox="0 0 50 40" width="30" height="24" fill="none">
        <path
          d="M25 20 C20 5, 2 5, 5 22 C7 30, 22 25, 25 22 Z"
          fill="url(#whiteGlow)"
          class="wing wing-left"
        />
        <path
          d="M25 20 C30 5, 48 5, 45 22 C43 30, 28 25, 25 22 Z"
          fill="url(#whiteGlow)"
          class="wing wing-right"
        />
        <ellipse cx="25" cy="21" rx="1.5" ry="6" fill="#ffffff" />
        <defs>
          <linearGradient id="whiteGlow" x1="0%" y1="0%" x2="100%" y2="100%">
            <stop offset="0%" stop-color="#ffffff" stop-opacity="0.95" />
            <stop offset="50%" stop-color="#e0f2fe" stop-opacity="0.85" />
            <stop offset="100%" stop-color="#93c5fd" stop-opacity="0.5" />
          </linearGradient>
        </defs>
      </svg>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const sparkles = ref([])
const petals = ref([])
const butterflies = ref([])

onMounted(() => {
  // Sparkles (optimized for mobile)
  sparkles.value = Array.from({ length: 8 }, (_, i) => ({
    id: i,
    x: Math.random() * 92 + 4,
    y: Math.random() * 90 + 5,
    size: Math.random() * 3 + 2,
    duration: Math.random() * 3 + 3,
    delay: Math.random() * 3,
    opacity: Math.random() * 0.6 + 0.3
  }))

  // Petals (optimized for mobile)
  petals.value = Array.from({ length: 5 }, (_, i) => ({
    id: i,
    x: Math.random() * 90 + 5,
    size: Math.random() * 6 + 6,
    duration: Math.random() * 6 + 8,
    delay: Math.random() * 6,
    rotation: Math.random() * 360,
    color: i % 2 === 0 ? 'white-petal' : 'blue-petal'
  }))

  // Glowing white butterflies (optimized for mobile)
  butterflies.value = [
    { id: 1, x: 18, y: 76, duration: 9, delay: 0, scale: 0.8 },
    { id: 2, x: 78, y: 78, duration: 11, delay: 2.5, scale: 0.7 }
  ]
})
</script>

<style scoped>
.particles-container {
  position: absolute;
  inset: 0;
  overflow: hidden;
  pointer-events: none;
  z-index: 10;
}

/* Sparkles */
.sparkle-particle {
  position: absolute;
  border-radius: 50%;
  background: radial-gradient(circle, #ffffff 0%, #93c5fd 60%, transparent 100%);
  box-shadow: 0 0 6px rgba(255, 255, 255, 0.8), 0 0 12px rgba(147, 197, 253, 0.7);
  animation: sparkleTwinkle ease-in-out infinite alternate;
  will-change: transform, opacity;
  transform: translate3d(0, 0, 0);
}

@keyframes sparkleTwinkle {
  0% {
    transform: translate3d(0, 0, 0) scale(0.4);
    opacity: 0.15;
  }
  100% {
    transform: translate3d(0, -12px, 0) scale(1.1);
    opacity: 0.9;
  }
}

/* Petals */
.drifting-petal {
  position: absolute;
  top: -20px;
  border-radius: 60% 40% 70% 30% / 50% 60% 40% 50%;
  animation: petalFall linear infinite;
  will-change: transform, opacity;
  transform: translate3d(0, 0, 0);
}

.white-petal {
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.9) 0%, rgba(240, 249, 255, 0.6) 100%);
  box-shadow: 0 0 4px rgba(255, 255, 255, 0.4);
}

.blue-petal {
  background: linear-gradient(135deg, rgba(96, 165, 250, 0.8) 0%, rgba(37, 99, 235, 0.5) 100%);
  box-shadow: 0 0 4px rgba(59, 130, 246, 0.35);
}

@keyframes petalFall {
  0% {
    top: -5%;
    transform: translate3d(0, 0, 0) rotate(0deg);
    opacity: 0;
  }
  12% {
    opacity: 0.85;
  }
  50% {
    transform: translate3d(24px, 45vh, 0) rotate(180deg);
    opacity: 0.9;
  }
  88% {
    opacity: 0.7;
  }
  100% {
    top: 105%;
    transform: translate3d(-18px, 95vh, 0) rotate(360deg);
    opacity: 0;
  }
}

/* Butterflies */
.ethereal-butterfly {
  position: absolute;
  filter: drop-shadow(0 0 6px rgba(255, 255, 255, 0.8));
  animation: butterflyFloat ease-in-out infinite;
  will-change: transform;
  transform: translate3d(0, 0, 0);
}

.wing {
  transform-origin: 25px 20px;
  animation: wingFlap 0.45s ease-in-out infinite alternate;
  will-change: transform;
}

.wing-right {
  animation-delay: 0.05s;
}

@keyframes wingFlap {
  0% {
    transform: scaleX(1);
  }
  100% {
    transform: scaleX(0.4);
  }
}

@keyframes butterflyFloat {
  0% {
    transform: translate3d(0, 0, 0) scale(0.8) rotate(0deg);
  }
  50% {
    transform: translate3d(14px, -18px, 0) scale(0.85) rotate(6deg);
  }
  100% {
    transform: translate3d(0, 0, 0) scale(0.8) rotate(0deg);
  }
}
</style>
