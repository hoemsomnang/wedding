<template>
  <div class="save-the-date-container">
    <div class="save-the-date-card">
      <!-- Background Floral & Gazebo Layer -->
      <div class="page-bg-layer">
        <img
          :src="altarBgUrl"
          alt="Wedding Altar Background"
          class="page-bg-img"
        />
        <div class="page-lighting-overlay"></div>
      </div>

      <!-- Particle Effects Layer -->
      <ParticleEffects />

      <!-- Flying Vector Bluebirds Layer (Scalable Vector SVG) -->
      <BirdFlockEffect />

      <!-- Main Typography & Content -->
      <div class="page-content">
        <!-- Top Spacer to align names in clear sky -->
        <div class="top-spacer"></div>

        <!-- Couple Calligraphy Names in Khmer -->
        <div class="names-calligraphy-section">
          <div class="name-mark-wrapper">
            <span class="calligraphy-name name-mark">សំណាង</span>
          </div>
          
          <div class="ampersand-wrapper">
            <span class="calligraphy-ampersand">&</span>
          </div>

          <div class="name-thida-wrapper">
            <span class="calligraphy-name name-thida">សារ៉េន</span>
          </div>
        </div>

        <!-- Save The Date Subtitle & Date in Khmer -->
        <div class="date-section">
          <h2 class="save-the-date-title">ថ្ងៃសិរីមង្គលអាពាហ៍ពិពាហ៍</h2>
          <p class="wedding-date-text">១៣ មីនា ២០២៧</p>
        </div>

        <!-- Center / Bottom Gazebo View Area -->
        <div class="altar-spacer"></div>

        <!-- Bottom Action Bar / Audio Controls matching sambot.online bar -->
        <div class="bottom-action-bar">
          <button
            class="back-btn"
            @click="$emit('back-to-cover')"
            title="ត្រឡប់ទៅទំព័រដើម (Back to Cover)"
          >
            <svg viewBox="0 0 24 24" width="18" height="18" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M15 18l-6-6 6-6" />
            </svg>
          </button>

          <button
            class="sound-toggle-btn"
            :class="{ active: isPlaying }"
            @click="toggleMusic"
            title="បិទ/បើកតន្ត្រី (Music Toggle)"
          >
            <svg v-if="isPlaying" viewBox="0 0 24 24" width="20" height="20" fill="currentColor">
              <path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/>
            </svg>
            <svg v-else viewBox="0 0 24 24" width="20" height="20" fill="currentColor">
              <path d="M16.5 12c0-1.77-1.02-3.29-2.5-4.03v2.21l2.45 2.45c.03-.2.05-.41.05-.63zm2.5 0c0 .94-.2 1.82-.54 2.64l1.51 1.51C20.63 14.91 21 13.5 21 12c0-4.28-2.99-7.86-7-8.77v2.06c2.89.86 5 3.54 5 6.71zM4.27 3L3 4.27l4.73 4.73H3v6h4l5 5v-6.73l4.25 4.25c-.67.52-1.42.93-2.25 1.18v2.06c1.38-.31 2.63-.95 3.69-1.81L19.73 21 21 19.73l-9-9L4.27 3zM12 4L9.91 6.09 12 8.18V4z"/>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ParticleEffects from './ParticleEffects.vue'
import BirdFlockEffect from './BirdFlockEffect.vue'
import altarBgUrl from '../assets/wedding_altar_bg.jpg'

const emit = defineEmits(['back-to-cover'])

const isPlaying = ref(false)
let audio = null

function toggleMusic() {
  if (!audio) {
    // Romantic ambient acoustic guitar / traditional soft wedding harp melody
    audio = new Audio('https://assets.mixkit.co/music/preview/mixkit-wedding-dream-150.mp3')
    audio.loop = true
  }

  if (isPlaying.value) {
    audio.pause()
    isPlaying.value = false
  } else {
    audio.play().then(() => {
      isPlaying.value = true
    }).catch(e => console.log('Audio autoplay prevented:', e))
  }
}
</script>

<style scoped>
.save-the-date-container {
  width: 100vw;
  height: 100vh;
  height: 100dvh;
  max-width: 100%;
  padding: 0;
  margin: 0;
  overflow: hidden;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #0b132b;
}

.save-the-date-card {
  position: relative;
  width: 100%;
  height: 100%;
  max-height: 100%;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

/* Background Layer */
.page-bg-layer {
  position: absolute;
  inset: 0;
  z-index: 1;
}

.page-bg-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  display: block;
}

.page-lighting-overlay {
  position: absolute;
  inset: 0;
  background: radial-gradient(
    ellipse at 50% 30%,
    rgba(255, 255, 255, 0.45) 0%,
    rgba(240, 249, 255, 0.15) 55%,
    rgba(15, 23, 42, 0.1) 100%
  );
  pointer-events: none;
}

/* Main Content */
.page-content {
  position: relative;
  z-index: 20;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100%;
  width: 100%;
  padding: 2vh 20px 2.5vh 20px;
  text-align: center;
  box-sizing: border-box;
}

.top-spacer {
  height: 12vh;
  min-height: 70px;
}

/* Calligraphy Names Section */
.names-calligraphy-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  width: 100%;
}

.name-mark-wrapper {
  position: relative;
  transform: translateX(-22px);
  animation: calligraphyRevealTop 1.1s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

.name-thida-wrapper {
  position: relative;
  transform: translateX(25px) translateY(-14px);
  animation: calligraphyRevealBottom 1.25s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

.ampersand-wrapper {
  position: absolute;
  top: 42%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 5;
  animation: ampersandSpin 1.3s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

.calligraphy-name {
  font-family: var(--font-moul), 'Kantumruy Pro', serif;
  font-size: 2.35rem;
  font-weight: 400;
  line-height: 1.35;
  color: #0b2559;
  background: linear-gradient(180deg, #071a3d 0%, #0e306e 40%, #1d4ed8 75%, #0b2559 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: 
    drop-shadow(0 1px 0 #ffffff)
    drop-shadow(0 -0.8px 0 rgba(255, 255, 255, 0.9))
    drop-shadow(0.8px 0 0 rgba(255, 255, 255, 0.8))
    drop-shadow(-0.8px 0 0 rgba(255, 255, 255, 0.8))
    drop-shadow(0 4px 14px rgba(11, 37, 89, 0.4));
  display: inline-block;
  letter-spacing: 0.5px;
  position: relative;
}

.calligraphy-ampersand {
  font-family: 'Cinzel', 'Playfair Display', serif;
  font-size: 2rem;
  font-weight: 700;
  color: #1e3a8a;
  filter: drop-shadow(0 2px 5px rgba(255, 255, 255, 0.9));
  opacity: 0.9;
}

/* Save the Date Section */
.date-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
  margin-top: 2vh;
  animation: fadeInDate 1.4s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

.save-the-date-title {
  font-family: var(--font-moul), serif;
  font-size: 1.15rem;
  font-weight: 400;
  letter-spacing: 0.5px;
  line-height: 1.4;
  color: #0e2b5c;
  background: linear-gradient(180deg, #09234e 0%, #164696 50%, #2563eb 80%, #0e2b5c 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: 
    drop-shadow(0 1px 0 #ffffff)
    drop-shadow(0 3px 8px rgba(14, 43, 92, 0.3));
}

.wedding-date-text {
  font-family: 'Kantumruy Pro', var(--font-body);
  font-size: 1.18rem;
  font-weight: 700;
  letter-spacing: 1px;
  color: #12346d;
  text-shadow: 0 1px 2px rgba(255, 255, 255, 0.9);
}

.altar-spacer {
  flex: 1;
}

/* Bottom Action Bar */
.bottom-action-bar {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 12px;
  margin-bottom: 1vh;
  z-index: 30;
}

.back-btn, .sound-toggle-btn {
  width: 38px;
  height: 38px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.75);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  border: 1px solid rgba(255, 255, 255, 0.9);
  color: #0e2b5c;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 0 4px 12px rgba(15, 23, 42, 0.15);
  transition: all 0.25s ease;
}

.back-btn:hover, .sound-toggle-btn:hover {
  background: rgba(255, 255, 255, 0.95);
  transform: scale(1.08);
  box-shadow: 0 6px 16px rgba(37, 99, 235, 0.25);
}

.sound-toggle-btn.active {
  background: #1e40af;
  color: #ffffff;
  border-color: #3b82f6;
  box-shadow: 0 0 14px rgba(37, 99, 235, 0.5);
}

/* Animations */
@keyframes calligraphyRevealTop {
  0% {
    opacity: 0;
    transform: translateX(-22px) translateY(-30px) scale(0.9);
    filter: blur(8px);
  }
  100% {
    opacity: 1;
    transform: translateX(-22px) translateY(0) scale(1);
    filter: blur(0);
  }
}

@keyframes calligraphyRevealBottom {
  0% {
    opacity: 0;
    transform: translateX(25px) translateY(20px) scale(0.9);
    filter: blur(8px);
  }
  100% {
    opacity: 1;
    transform: translateX(25px) translateY(-14px) scale(1);
    filter: blur(0);
  }
}

@keyframes ampersandSpin {
  0% {
    opacity: 0;
    transform: translate(-50%, -50%) scale(0.4) rotate(-30deg);
  }
  100% {
    opacity: 0.9;
    transform: translate(-50%, -50%) scale(1) rotate(0deg);
  }
}

@keyframes fadeInDate {
  0% {
    opacity: 0;
    transform: translateY(20px);
    letter-spacing: 7px;
  }
  100% {
    opacity: 1;
    transform: translateY(0);
    letter-spacing: 4px;
  }
}

/* Responsive */
@media (max-height: 700px) {
  .top-spacer {
    height: 8vh;
    min-height: 45px;
  }
  .calligraphy-name {
    font-size: 1.95rem;
  }
  .save-the-date-title {
    font-size: 1rem;
  }
  .wedding-date-text {
    font-size: 1.05rem;
  }
}

@media (min-width: 480px) and (min-height: 800px) {
  .calligraphy-name {
    font-size: 2.6rem;
  }
  .save-the-date-title {
    font-size: 1.25rem;
  }
  .wedding-date-text {
    font-size: 1.28rem;
  }
}
</style>
