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

    <!-- Glowing White Ethereal Butterflies Flying Across Viewport -->
    <div
      v-for="butterfly in butterflies"
      :key="'butterfly-' + butterfly.id"
      class="butterfly-tracker"
      :class="butterfly.flightClass"
      :style="{
        animationDuration: butterfly.duration + 's',
        animationDelay: butterfly.delay + 's'
      }"
    >
      <div class="butterfly-graphic">
        <svg class="butterfly-svg" viewBox="0 0 50 40" width="34" height="28" fill="none">
          <path
            d="M25 20 C20 4, 2 4, 5 22 C7 30, 22 26, 25 22 Z"
            fill="url(#whiteGlow)"
            stroke="#ffffff"
            stroke-width="0.8"
            class="wing wing-left"
          />
          <path
            d="M25 20 C30 4, 48 4, 45 22 C43 30, 28 26, 25 22 Z"
            fill="url(#whiteGlow)"
            stroke="#ffffff"
            stroke-width="0.8"
            class="wing wing-right"
          />
          <ellipse cx="25" cy="21" rx="1.6" ry="6" fill="#1e293b" />
          <path d="M24 15 C22 10, 18 8, 16 7" stroke="#93c5fd" stroke-width="0.7" stroke-linecap="round" />
          <path d="M26 15 C28 10, 32 8, 34 7" stroke="#93c5fd" stroke-width="0.7" stroke-linecap="round" />
          <defs>
            <linearGradient id="whiteGlow" x1="0%" y1="0%" x2="100%" y2="100%">
              <stop offset="0%" stop-color="#ffffff" stop-opacity="0.98" />
              <stop offset="50%" stop-color="#f0f9ff" stop-opacity="0.9" />
              <stop offset="100%" stop-color="#93c5fd" stop-opacity="0.65" />
            </linearGradient>
          </defs>
        </svg>
      </div>
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

  // 4 Glowing White Butterflies flying across the screen from different directions
  butterflies.value = [
    { id: 1, duration: 14, delay: 0, flightClass: 'butterfly-cross-1' },
    { id: 2, duration: 16, delay: 3.5, flightClass: 'butterfly-cross-2' },
    { id: 3, duration: 13, delay: 7.0, flightClass: 'butterfly-cross-3' },
    { id: 4, duration: 15, delay: 10.5, flightClass: 'butterfly-cross-4' }
  ]
})
</script>

<style lang="scss" scoped>
.particles-container {
  position: absolute;
  inset: 0;
  overflow: hidden;
  pointer-events: none;
  z-index: 20;
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

/* Butterflies System Flying Across the Screen */
.butterfly-tracker {
  position: absolute;
  top: 0;
  left: 0;
  pointer-events: none;
  will-change: transform;

  &.butterfly-cross-1 {
    animation: flightAcross1 linear infinite;
  }

  &.butterfly-cross-2 {
    animation: flightAcross2 linear infinite;
  }

  &.butterfly-cross-3 {
    animation: flightAcross3 linear infinite;
  }

  &.butterfly-cross-4 {
    animation: flightAcross4 linear infinite;
  }
}

.butterfly-graphic {
  filter: drop-shadow(0 0 8px rgba(255, 255, 255, 0.95)) drop-shadow(0 2px 6px rgba(15, 35, 75, 0.35));
  animation: bodyFlutter 0.8s ease-in-out infinite alternate;
}

.butterfly-svg {
  display: block;
  overflow: visible;
}

.wing {
  transform-origin: 25px 20px;
  animation: wingFlap 0.28s ease-in-out infinite alternate;
  will-change: transform;
}

.wing-right {
  animation-delay: 0.03s;
}

@keyframes wingFlap {
  0% {
    transform: scaleX(1);
  }
  100% {
    transform: scaleX(0.28);
  }
}

@keyframes bodyFlutter {
  0% {
    transform: translateY(0) rotate(-3deg);
  }
  100% {
    transform: translateY(-6px) rotate(4deg);
  }
}

/* Butterfly Trajectory Animations across the Viewport */

// Path 1: Left to Right ascending wave (starts lower left, rises across center sky)
@keyframes flightAcross1 {
  0% {
    transform: translate3d(-12vw, 68vh, 0) scale(0.75) rotate(10deg);
    opacity: 0;
  }
  6% {
    opacity: 1;
    transform: translate3d(4vw, 62vh, 0) scale(0.85) rotate(14deg);
  }
  30% {
    transform: translate3d(32vw, 48vh, 0) scale(0.92) rotate(-4deg);
  }
  55% {
    transform: translate3d(58vw, 38vh, 0) scale(0.85) rotate(8deg);
  }
  80% {
    transform: translate3d(84vw, 24vh, 0) scale(0.88) rotate(-6deg);
    opacity: 1;
  }
  94% {
    opacity: 0.9;
  }
  100% {
    transform: translate3d(112vw, 15vh, 0) scale(0.75) rotate(4deg);
    opacity: 0;
  }
}

// Path 2: Right to Left mid-sky gentle swoop (starts right, glides across middle)
@keyframes flightAcross2 {
  0% {
    transform: translate3d(112vw, 48vh, 0) scaleX(-1) scale(0.72) rotate(-8deg);
    opacity: 0;
  }
  6% {
    opacity: 1;
    transform: translate3d(95vw, 42vh, 0) scaleX(-1) scale(0.8) rotate(-12deg);
  }
  35% {
    transform: translate3d(62vw, 54vh, 0) scaleX(-1) scale(0.86) rotate(6deg);
  }
  65% {
    transform: translate3d(32vw, 36vh, 0) scaleX(-1) scale(0.78) rotate(-8deg);
  }
  85% {
    transform: translate3d(8vw, 44vh, 0) scaleX(-1) scale(0.82) rotate(4deg);
    opacity: 1;
  }
  95% {
    opacity: 0.85;
  }
  100% {
    transform: translate3d(-14vw, 30vh, 0) scaleX(-1) scale(0.72) rotate(-5deg);
    opacity: 0;
  }
}

// Path 3: Upper sky dancing drift (starts left upper sky, dances across upper clouds)
@keyframes flightAcross3 {
  0% {
    transform: translate3d(-12vw, 26vh, 0) scale(0.7) rotate(6deg);
    opacity: 0;
  }
  8% {
    opacity: 1;
    transform: translate3d(6vw, 20vh, 0) scale(0.8) rotate(12deg);
  }
  40% {
    transform: translate3d(42vw, 28vh, 0) scale(0.85) rotate(-6deg);
  }
  70% {
    transform: translate3d(74vw, 14vh, 0) scale(0.78) rotate(10deg);
    opacity: 1;
  }
  92% {
    opacity: 0.9;
  }
  100% {
    transform: translate3d(112vw, 8vh, 0) scale(0.7) rotate(2deg);
    opacity: 0;
  }
}

// Path 4: Lower floral garden swoop (starts right lower, swoops across gazebo garden)
@keyframes flightAcross4 {
  0% {
    transform: translate3d(112vw, 76vh, 0) scaleX(-1) scale(0.75) rotate(8deg);
    opacity: 0;
  }
  6% {
    opacity: 1;
    transform: translate3d(92vw, 70vh, 0) scaleX(-1) scale(0.82) rotate(10deg);
  }
  38% {
    transform: translate3d(55vw, 60vh, 0) scaleX(-1) scale(0.88) rotate(-8deg);
  }
  72% {
    transform: translate3d(24vw, 68vh, 0) scaleX(-1) scale(0.8) rotate(6deg);
    opacity: 1;
  }
  94% {
    opacity: 0.85;
  }
  100% {
    transform: translate3d(-14vw, 54vh, 0) scaleX(-1) scale(0.75) rotate(-4deg);
    opacity: 0;
  }
}
</style>
