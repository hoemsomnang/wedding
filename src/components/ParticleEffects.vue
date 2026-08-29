<template>
  <div class="particles-container" aria-hidden="true">
    <!-- Flying Bluebirds Flock (matching photo 1) -->
    <div
      v-for="bird in flyingBirds"
      :key="'bird-' + bird.id"
      class="flying-bird"
      :style="{
        left: bird.x + '%',
        top: bird.y + '%',
        animationDuration: bird.duration + 's',
        animationDelay: bird.delay + 's',
        transform: `scale(${bird.scale}) rotate(${bird.angle}deg)`
      }"
    >
      <svg class="bird-svg" viewBox="0 0 100 80" width="46" height="38">
        <!-- Left Wing -->
        <path
          d="M 50 40 Q 25 5 0 20 Q 20 40 45 42 Z"
          fill="url(#blueFeatherGrad)"
          class="bird-wing wing-l"
        />
        <!-- Right Wing -->
        <path
          d="M 50 40 Q 75 5 100 20 Q 80 40 55 42 Z"
          fill="url(#blueFeatherGrad)"
          class="bird-wing wing-r"
        />
        <!-- Bird Body & Head -->
        <ellipse cx="50" cy="42" rx="6" ry="16" fill="#1d4ed8" />
        <ellipse cx="50" cy="43" rx="4" ry="12" fill="#dbeafe" />
        <circle cx="50" cy="27" r="5" fill="#1e3a8a" />
        <!-- Tail -->
        <path d="M 46 54 L 50 72 L 54 54 Z" fill="#2563eb" />
        <defs>
          <linearGradient id="blueFeatherGrad" x1="0%" y1="0%" x2="100%" y2="100%">
            <stop offset="0%" stop-color="#38bdf8" />
            <stop offset="50%" stop-color="#2563eb" />
            <stop offset="100%" stop-color="#1e3a8a" />
          </linearGradient>
        </defs>
      </svg>
    </div>

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

    <!-- Glowing White Butterflies / Doves near bottom -->
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
      <svg class="butterfly-svg" viewBox="0 0 50 40" width="34" height="28" fill="none">
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
const flyingBirds = ref([])

onMounted(() => {
  // Generate flying blue birds matching image 1
  flyingBirds.value = [
    { id: 1, x: 42, y: 28, duration: 9, delay: 0, scale: 1.1, angle: -12 },
    { id: 2, x: 20, y: 44, duration: 11, delay: 1.2, scale: 0.85, angle: 18 },
    { id: 3, x: 68, y: 42, duration: 10, delay: 0.8, scale: 0.9, angle: -15 },
    { id: 4, x: 32, y: 55, duration: 12, delay: 2.5, scale: 0.75, angle: 25 },
    { id: 5, x: 74, y: 60, duration: 10.5, delay: 1.8, scale: 0.8, angle: -20 },
    { id: 6, x: 48, y: 68, duration: 13, delay: 3.2, scale: 0.65, angle: 10 }
  ]

  // Sparkles
  sparkles.value = Array.from({ length: 22 }, (_, i) => ({
    id: i,
    x: Math.random() * 100,
    y: Math.random() * 100,
    size: Math.random() * 4 + 2,
    duration: Math.random() * 4 + 3,
    delay: Math.random() * 5,
    opacity: Math.random() * 0.7 + 0.3
  }))

  // Petals
  petals.value = Array.from({ length: 14 }, (_, i) => ({
    id: i,
    x: Math.random() * 95,
    size: Math.random() * 9 + 7,
    duration: Math.random() * 8 + 7,
    delay: Math.random() * 8,
    rotation: Math.random() * 360,
    color: i % 3 === 0 ? 'white-petal' : i % 3 === 1 ? 'blue-petal' : 'sky-petal'
  }))

  // Glowing white butterflies
  butterflies.value = [
    { id: 1, x: 16, y: 74, duration: 8, delay: 0, scale: 0.85 },
    { id: 2, x: 80, y: 72, duration: 9.5, delay: 1.8, scale: 0.75 },
    { id: 3, x: 30, y: 84, duration: 11, delay: 3.2, scale: 0.9 },
    { id: 4, x: 68, y: 86, duration: 10, delay: 4.5, scale: 0.7 }
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

/* Flying Blue Birds (from Photo 1) */
.flying-bird {
  position: absolute;
  filter: drop-shadow(0 4px 10px rgba(30, 64, 175, 0.4));
  animation: birdSwoop linear infinite;
}

.bird-wing {
  transform-origin: 50px 40px;
  animation: birdFlap 0.4s ease-in-out infinite alternate;
}

.wing-l {
  animation-delay: 0s;
}

.wing-r {
  animation-delay: 0.05s;
}

@keyframes birdFlap {
  0% {
    transform: scaleY(1);
  }
  100% {
    transform: scaleY(-0.4);
  }
}

@keyframes birdSwoop {
  0% {
    transform: translate(0, 0) scale(1) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: 0.85;
  }
  50% {
    transform: translate(25px, -35px) scale(1.05) rotate(12deg);
    opacity: 0.95;
  }
  90% {
    opacity: 0.75;
  }
  100% {
    transform: translate(60px, -80px) scale(0.9) rotate(20deg);
    opacity: 0;
  }
}

/* Sparkles */
.sparkle-particle {
  position: absolute;
  border-radius: 50%;
  background: radial-gradient(circle, #ffffff 0%, #93c5fd 60%, transparent 100%);
  box-shadow: 0 0 8px rgba(255, 255, 255, 0.9), 0 0 16px rgba(147, 197, 253, 0.8);
  animation: sparkleTwinkle ease-in-out infinite alternate;
}

@keyframes sparkleTwinkle {
  0% {
    transform: scale(0.3) translateY(0);
    opacity: 0.1;
  }
  50% {
    transform: scale(1.3) translateY(-10px);
    opacity: 0.95;
  }
  100% {
    transform: scale(0.4) translateY(-20px);
    opacity: 0.1;
  }
}

/* Petals */
.drifting-petal {
  position: absolute;
  top: -20px;
  border-radius: 60% 40% 70% 30% / 50% 60% 40% 50%;
  filter: blur(0.3px);
  animation: petalFall linear infinite;
}

.white-petal {
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.9) 0%, rgba(240, 249, 255, 0.6) 100%);
  box-shadow: 0 0 6px rgba(255, 255, 255, 0.5);
}

.blue-petal {
  background: linear-gradient(135deg, rgba(96, 165, 250, 0.8) 0%, rgba(37, 99, 235, 0.5) 100%);
  box-shadow: 0 0 6px rgba(59, 130, 246, 0.4);
}

.sky-petal {
  background: linear-gradient(135deg, rgba(186, 230, 253, 0.85) 0%, rgba(147, 197, 253, 0.5) 100%);
}

@keyframes petalFall {
  0% {
    top: -5%;
    transform: translateX(0) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: 0.85;
  }
  50% {
    transform: translateX(35px) rotate(180deg);
    opacity: 0.9;
  }
  90% {
    opacity: 0.7;
  }
  100% {
    top: 105%;
    transform: translateX(-25px) rotate(360deg);
    opacity: 0;
  }
}

/* Butterflies */
.ethereal-butterfly {
  position: absolute;
  filter: drop-shadow(0 0 8px rgba(255, 255, 255, 0.8)) drop-shadow(0 0 15px rgba(147, 197, 253, 0.6));
  animation: butterflyFloat ease-in-out infinite;
}

.wing {
  transform-origin: 25px 20px;
  animation: wingFlap 0.45s ease-in-out infinite alternate;
}

.wing-right {
  animation-delay: 0.05s;
}

@keyframes wingFlap {
  0% {
    transform: scaleX(1);
  }
  100% {
    transform: scaleX(0.35);
  }
}

@keyframes butterflyFloat {
  0% {
    transform: translate(0, 0) scale(var(--scale, 0.8)) rotate(0deg);
  }
  30% {
    transform: translate(15px, -20px) scale(var(--scale, 0.85)) rotate(8deg);
  }
  60% {
    transform: translate(-10px, -35px) scale(var(--scale, 0.75)) rotate(-6deg);
  }
  100% {
    transform: translate(0, 0) scale(var(--scale, 0.8)) rotate(0deg);
  }
}
</style>
