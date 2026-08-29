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

      <!-- Twinkling Fairy Light Bulbs across Arch Curtain -->
      <div class="fairy-lights-garland" aria-hidden="true">
        <div v-for="i in 16" :key="'fairy-light-' + i" :class="'fairy-light-bulb bulb-' + i"></div>
      </div>

      <!-- Warm Golden Lantern Glows at bottom walkway -->
      <div class="lantern-glows-layer" aria-hidden="true">
        <div class="lantern-glow-point lantern-left"></div>
        <div class="lantern-glow-point lantern-right"></div>
      </div>

      <!-- Particle Effects Layer (Petals, Butterflies, Sparkles) -->
      <ParticleEffects />

      <!-- Flying Vector Bluebirds Layer (Scalable Vector SVG) -->
      <BirdFlockEffect />

      <!-- Main Typography & Content -->
      <div class="page-content">
        <!-- Top Spacer -->
        <div class="top-spacer"></div>

        <!-- Glassmorphic Royal Crest Container -->
        <div class="royal-names-card">
          <!-- Monogram Crown Emblem -->
          <div class="crown-emblem">
            <svg viewBox="0 0 60 24" width="48" height="20" fill="none">
              <path d="M5 20 L15 6 L30 16 L45 6 L55 20 Z" fill="url(#goldCrownGrad)" stroke="#d4af37" stroke-width="1"/>
              <circle cx="15" cy="5" r="2.5" fill="#fef08a" />
              <circle cx="30" cy="14" r="2.5" fill="#fef08a" />
              <circle cx="45" cy="5" r="2.5" fill="#fef08a" />
              <defs>
                <linearGradient id="goldCrownGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                  <stop offset="0%" stop-color="#fef08a" />
                  <stop offset="50%" stop-color="#d4af37" />
                  <stop offset="100%" stop-color="#996515" />
                </linearGradient>
              </defs>
            </svg>
          </div>

          <!-- Couple Calligraphy Names in Authentic Khmer -->
          <div class="names-calligraphy-section">
            <div class="name-mark-wrapper">
              <span class="calligraphy-name name-mark">សំណាង</span>
            </div>
            
            <div class="ampersand-divider-wrapper">
              <span class="gold-filigree-line left-line"></span>
              <span class="calligraphy-ampersand">&</span>
              <span class="gold-filigree-line right-line"></span>
            </div>

            <div class="name-thida-wrapper">
              <span class="calligraphy-name name-thida">សារ៉េន</span>
            </div>
          </div>

          <!-- Ornate Gold Divider -->
          <div class="ornate-gold-divider">
            <span class="divider-diamond">❖</span>
            <span class="divider-line"></span>
            <span class="divider-crown">❦</span>
            <span class="divider-line"></span>
            <span class="divider-diamond">❖</span>
          </div>

          <!-- Save The Date Subtitle in Khmer -->
          <div class="date-section">
            <h2 class="save-the-date-title">ថ្ងៃសិរីមង្គលអាពាហ៍ពិពាហ៍</h2>
            
            <!-- Luxury Date Pill Badge -->
            <div class="wedding-date-badge">
              <div class="badge-shine"></div>
              <span class="date-khmer-text">ថ្ងៃសៅរ៍ ទី១៣ ខែមីនា ឆ្នាំ២០២៧</span>
              <span class="date-sub-en">13 . 03 . 2027</span>
            </div>
          </div>

          <!-- Live Wedding Countdown Timer -->
          <div class="countdown-container">
            <div class="countdown-item">
              <span class="countdown-num">{{ countdown.days }}</span>
              <span class="countdown-label">ថ្ងៃ (Days)</span>
            </div>
            <span class="countdown-sep">:</span>
            <div class="countdown-item">
              <span class="countdown-num">{{ countdown.hours }}</span>
              <span class="countdown-label">ម៉ោង (Hours)</span>
            </div>
            <span class="countdown-sep">:</span>
            <div class="countdown-item">
              <span class="countdown-num">{{ countdown.minutes }}</span>
              <span class="countdown-label">នាទី (Mins)</span>
            </div>
            <span class="countdown-sep">:</span>
            <div class="countdown-item">
              <span class="countdown-num">{{ countdown.seconds }}</span>
              <span class="countdown-label">វិនាទី (Secs)</span>
            </div>
          </div>
        </div>

        <!-- Altar Spacer -->
        <div class="altar-spacer"></div>

        <!-- Bottom Action Bar / Audio Controls -->
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
import { ref, onMounted, onUnmounted } from 'vue'
import ParticleEffects from './ParticleEffects.vue'
import BirdFlockEffect from './BirdFlockEffect.vue'
import altarBgUrl from '../assets/wedding_altar_bg.jpg'

const emit = defineEmits(['back-to-cover'])

const isPlaying = ref(false)
let audio = null

// Live Countdown Timer to 13 March 2027
const targetDate = new Date('2027-03-13T09:00:00')
const countdown = ref({ days: '000', hours: '00', minutes: '00', seconds: '00' })
let timer = null

function updateCountdown() {
  const now = new Date()
  const diff = targetDate - now
  if (diff > 0) {
    const days = Math.floor(diff / (1000 * 60 * 60 * 24))
    const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
    const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60))
    const seconds = Math.floor((diff % (1000 * 60)) / 1000)

    countdown.value = {
      days: String(days).padStart(3, '0'),
      hours: String(hours).padStart(2, '0'),
      minutes: String(minutes).padStart(2, '0'),
      seconds: String(seconds).padStart(2, '0')
    }
  }
}

onMounted(() => {
  updateCountdown()
  timer = setInterval(updateCountdown, 1000)
})

onUnmounted(() => {
  if (timer) clearInterval(timer)
})

function toggleMusic() {
  if (!audio) {
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

<style lang="scss" scoped>
$gold-primary: #d4af37;
$gold-light: #fef08a;
$sapphire-dark: #071a3d;
$sapphire-primary: #1d4ed8;

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
    ellipse at 50% 25%,
    rgba(255, 255, 255, 0.4) 0%,
    rgba(240, 249, 255, 0.1) 50%,
    rgba(15, 23, 42, 0.15) 100%
  );
  pointer-events: none;
}

/* Twinkling Fairy Lights Garland across Arch */
.fairy-lights-garland {
  position: absolute;
  top: 38%;
  left: 0;
  right: 0;
  height: 80px;
  pointer-events: none;
  z-index: 5;
}

.fairy-light-bulb {
  position: absolute;
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: radial-gradient(circle, #fff 20%, #fef08a 60%, rgba(212, 175, 55, 0) 100%);
  box-shadow: 0 0 10px 3px rgba(254, 240, 138, 0.8), 0 0 20px 6px rgba(254, 240, 138, 0.4);
  animation: fairyLightTwinkle 2.5s ease-in-out infinite alternate;
}

@for $i from 1 through 16 {
  .bulb-#{$i} {
    left: #{($i * 5.8) + 2}%;
    top: #{sin($i * 0.4) * 22 + 25}px;
    animation-delay: #{($i * 0.18)}s;
    animation-duration: #{2.0 + ($i % 3) * 0.5}s;
  }
}

@keyframes fairyLightTwinkle {
  0% {
    opacity: 0.35;
    transform: scale(0.7);
  }
  100% {
    opacity: 1;
    transform: scale(1.3);
  }
}

/* Lantern Glow Points on Aisle Walkway */
.lantern-glows-layer {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 200px;
  pointer-events: none;
  z-index: 4;
}

.lantern-glow-point {
  position: absolute;
  bottom: 30px;
  width: 90px;
  height: 90px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(254, 240, 138, 0.6) 0%, rgba(212, 175, 55, 0.25) 45%, transparent 75%);
  filter: blur(12px);
  animation: lanternFlicker 3.2s ease-in-out infinite alternate;
}

.lantern-left {
  left: 12%;
}

.lantern-right {
  right: 12%;
  animation-delay: 1.2s;
}

@keyframes lanternFlicker {
  0% {
    opacity: 0.6;
    transform: scale(0.9);
  }
  100% {
    opacity: 1;
    transform: scale(1.15);
  }
}

/* Main Content Layout */
.page-content {
  position: relative;
  z-index: 20;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100%;
  width: 100%;
  padding: 1.5vh 16px 2vh 16px;
  text-align: center;
  box-sizing: border-box;
}

.top-spacer {
  height: 4vh;
  min-height: 25px;
}

/* Glassmorphic Royal Names Container */
.royal-names-card {
  position: relative;
  width: 100%;
  max-width: 440px;
  padding: 18px 16px 14px 16px;
  border-radius: 24px;
  background: radial-gradient(ellipse at 50% 30%, rgba(255, 255, 255, 0.82) 0%, rgba(240, 249, 255, 0.65) 60%, rgba(224, 242, 254, 0.4) 100%);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border: 1.5px solid rgba(255, 255, 255, 0.9);
  box-shadow: 
    0 15px 35px -8px rgba(14, 43, 92, 0.18),
    0 0 0 1px rgba(212, 175, 55, 0.25),
    inset 0 0 20px rgba(255, 255, 255, 0.8);
  animation: cardFadeIn 1.1s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

.crown-emblem {
  margin-bottom: 2px;
  display: flex;
  justify-content: center;
  filter: drop-shadow(0 2px 4px rgba(212, 175, 55, 0.4));
  animation: floatCrown 3.5s ease-in-out infinite alternate;
}

@keyframes floatCrown {
  0% { transform: translateY(0); }
  100% { transform: translateY(-3px); }
}

/* Calligraphy Names Section */
.names-calligraphy-section {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  width: 100%;
  margin: 4px 0 8px 0;
  flex-wrap: wrap;
}

.calligraphy-name {
  font-family: var(--font-moul), 'Kantumruy Pro', serif;
  font-size: 2.25rem;
  font-weight: 400;
  line-height: 1.35;
  color: #071a3d;
  background: linear-gradient(180deg, #071a3d 0%, #0e306e 40%, #1d4ed8 75%, #0b2559 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: 
    drop-shadow(0 1px 0 #ffffff)
    drop-shadow(0 -0.8px 0 rgba(255, 255, 255, 0.95))
    drop-shadow(0.8px 0 0 rgba(255, 255, 255, 0.9))
    drop-shadow(-0.8px 0 0 rgba(255, 255, 255, 0.9))
    drop-shadow(0 4px 12px rgba(11, 37, 89, 0.35));
  display: inline-block;
  letter-spacing: 0.5px;

  @media (max-width: 420px) {
    font-size: 1.85rem;
  }
}

.ampersand-divider-wrapper {
  display: flex;
  align-items: center;
  gap: 6px;
}

.gold-filigree-line {
  width: 16px;
  height: 1.5px;
  background: linear-gradient(90deg, transparent, #d4af37, #fef08a);

  &.right-line {
    background: linear-gradient(90deg, #fef08a, #d4af37, transparent);
  }
}

.calligraphy-ampersand {
  font-family: 'Cinzel', 'Playfair Display', serif;
  font-size: 1.7rem;
  font-weight: 700;
  color: #d4af37;
  background: linear-gradient(180deg, #fef08a 0%, #d4af37 60%, #996515 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: drop-shadow(0 1.5px 3px rgba(153, 101, 21, 0.35));
}

/* Ornate Gold Divider */
.ornate-gold-divider {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  margin: 4px 0 8px 0;
  color: #d4af37;
  font-size: 0.75rem;

  .divider-line {
    width: 45px;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(212, 175, 55, 0.8), transparent);
  }

  .divider-diamond {
    font-size: 0.75rem;
    color: #d4af37;
    filter: drop-shadow(0 0 4px rgba(254, 240, 138, 0.8));
  }

  .divider-crown {
    font-size: 0.95rem;
    color: #1d4ed8;
  }
}

/* Save the Date Title */
.date-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
}

.save-the-date-title {
  font-family: var(--font-moul), serif;
  font-size: 1.12rem;
  font-weight: 400;
  letter-spacing: 0.5px;
  line-height: 1.4;
  color: #0e2b5c;
  background: linear-gradient(180deg, #09234e 0%, #164696 50%, #2563eb 85%, #0e2b5c 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: 
    drop-shadow(0 1px 0 #ffffff)
    drop-shadow(0 2px 6px rgba(14, 43, 92, 0.25));

  @media (max-width: 420px) {
    font-size: 0.98rem;
  }
}

/* Luxury Date Pill Badge */
.wedding-date-badge {
  position: relative;
  display: inline-flex;
  flex-direction: column;
  align-items: center;
  padding: 6px 20px;
  border-radius: 999px;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.95) 0%, rgba(240, 249, 255, 0.85) 100%);
  border: 1.5px solid #d4af37;
  box-shadow: 
    0 4px 12px rgba(14, 43, 92, 0.12),
    inset 0 0 10px rgba(254, 240, 138, 0.35);
  overflow: hidden;
  margin-top: 3px;

  .date-khmer-text {
    font-family: 'Kantumruy Pro', var(--font-body);
    font-size: 1.05rem;
    font-weight: 700;
    color: #0b2559;
    letter-spacing: 0.3px;
  }

  .date-sub-en {
    font-family: 'Cinzel', serif;
    font-size: 0.72rem;
    font-weight: 700;
    color: #996515;
    letter-spacing: 2.5px;
    margin-top: 1px;
  }

  .badge-shine {
    position: absolute;
    top: 0;
    left: -100%;
    width: 60%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.8), transparent);
    transform: skewX(-25deg);
    animation: badgeShine 4.5s infinite;
  }
}

@keyframes badgeShine {
  0%, 65% { left: -100%; }
  100% { left: 200%; }
}

/* Live Countdown Timer */
.countdown-container {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  margin-top: 10px;
  padding-top: 8px;
  border-top: 1px dashed rgba(212, 175, 55, 0.35);
}

.countdown-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-width: 48px;
  padding: 3px 6px;
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.7);
  border: 1px solid rgba(212, 175, 55, 0.3);

  .countdown-num {
    font-family: 'Cinzel', monospace;
    font-size: 1.05rem;
    font-weight: 700;
    color: #0b2559;
    line-height: 1.1;
  }

  .countdown-label {
    font-family: 'Kantumruy Pro', sans-serif;
    font-size: 0.62rem;
    font-weight: 600;
    color: #78350f;
    margin-top: 2px;
  }
}

.countdown-sep {
  font-family: 'Cinzel', monospace;
  font-size: 1.1rem;
  font-weight: 700;
  color: #d4af37;
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
  margin-bottom: 0.5vh;
  z-index: 30;
}

.back-btn, .sound-toggle-btn {
  width: 42px;
  height: 42px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.88);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border: 1.5px solid rgba(212, 175, 55, 0.5);
  color: #0b2559;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 15px rgba(11, 37, 89, 0.2);
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);

  &:hover {
    transform: scale(1.08);
    background: #ffffff;
    border-color: #d4af37;
    box-shadow: 0 6px 20px rgba(212, 175, 55, 0.4);
  }

  &:active {
    transform: scale(0.95);
  }
}

.sound-toggle-btn.active {
  background: linear-gradient(135deg, #1d4ed8 0%, #0b2559 100%);
  color: #ffffff;
  border-color: #fef08a;
  box-shadow: 0 4px 15px rgba(29, 78, 216, 0.4);
}

@keyframes cardFadeIn {
  0% {
    opacity: 0;
    transform: translateY(20px) scale(0.95);
  }
  100% {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}
</style>
