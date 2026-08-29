<template>
  <div class="wedding-card-container">
    <!-- Card Frame Wrapper -->
    <div class="wedding-card" ref="cardRef">
      <!-- Background Floral Frame & Temple Scenery -->
      <div class="card-bg-layer">
        <img
          :src="floralBgUrl"
          alt="Floral Wedding Background"
          class="card-bg-img"
        />
        <div class="card-lighting-overlay"></div>
      </div>

      <!-- Particle Effects Layer (Falling Petals, Butterflies) -->
      <ParticleEffects />

      <!-- Flying Vector Bluebirds Layer (Scalable Vector SVG) -->
      <BirdFlockEffect />

      <!-- Main Content Area -->
      <div class="card-content" :class="{ 'is-opening': isOpening }">
        <!-- Top Monogram Section (Floating directly on sky, no circular container) -->
        <div class="monogram-section">
          <div class="monogram-ambient-glow"></div>
          <div class="monogram-wrapper">
            <img
              :src="monogramUrl"
              alt="Royal Sapphire Monogram M"
              class="monogram-pure-img"
            />
            <div class="monogram-shimmer"></div>
          </div>
        </div>

        <!-- Main Khmer Titles -->
        <div class="titles-section">
          <h1 class="main-title">សិរីមង្គលអាពាហ៍ពិពាហ៍</h1>
          <h2 class="sub-title">សូមគោរពអញ្ជើញ</h2>
        </div>

        <!-- Center Sky Spacer (allowing flowers and sky to breathe) -->
        <div class="center-spacer"></div>

        <!-- Guest Section -->
        <div class="guest-section">
          <div class="guest-label">ភ្ញៀវកិត្តិយស</div>
          <div class="guest-underline-area">
            <span class="guest-name" v-if="guestName">{{ guestName }}</span>
            <div class="guest-line"></div>
          </div>
        </div>

        <!-- Ornate Vintage Invitation Button (matching Photo 2) -->
        <div class="button-section">
          <button
            class="open-invitation-btn"
            @click="handleOpenInvitation"
            aria-label="សូមចុចបើកសំបុត្រ - Click to Open The Invitation"
            :disabled="isOpening"
          >
            <!-- Vintage Ornamental Curved Ears / Tabs -->
            <div class="btn-ear left-ear"></div>
            <div class="btn-ear right-ear"></div>

            <!-- Inner Double Border & Text -->
            <div class="btn-inner-border">
              <span class="btn-text-km">សូមចុចបើកសំបុត្រ</span>
              <span class="btn-text-en">Click to Open The Invitation</span>
            </div>

            <!-- Light shimmer animation -->
            <div class="btn-shine"></div>
          </button>
        </div>

        <!-- Bottom Buffer for temple & bottom hydrangeas -->
        <div class="bottom-buffer"></div>
      </div>

      <!-- Celestial Sunburst Light Explosion Overlay (matching video frame 12) -->
      <div v-if="isOpening" class="celestial-burst-overlay">
        <div class="sunburst-core"></div>
        <div class="sunburst-ring"></div>
        <div class="sunburst-rays"></div>
        <div class="diamond-stars-field">
          <div v-for="n in 12" :key="'star-' + n" :class="'star-point star-' + n"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import ParticleEffects from './ParticleEffects.vue'
import BirdFlockEffect from './BirdFlockEffect.vue'
import floralBgUrl from '../assets/wedding_floral_bg.jpg'
import rawMonogramUrl from '../assets/sapphire_m_crest_pure.jpg'
import confetti from 'canvas-confetti'

const props = defineProps({
  guestName: {
    type: String,
    default: ''
  }
})

const emit = defineEmits(['open-invitation'])

const cardRef = ref(null)
const monogramUrl = ref(rawMonogramUrl)
const isOpening = ref(false)

// Cut out pure white background to make a pristine transparent PNG
function processTransparentImage(src) {
  const img = new Image()
  img.src = src
  img.onload = () => {
    const canvas = document.createElement('canvas')
    canvas.width = img.naturalWidth || 600
    canvas.height = img.naturalHeight || 600
    const ctx = canvas.getContext('2d')
    ctx.drawImage(img, 0, 0, canvas.width, canvas.height)
    
    const imgData = ctx.getImageData(0, 0, canvas.width, canvas.height)
    const data = imgData.data
    
    for (let i = 0; i < data.length; i += 4) {
      const r = data[i]
      const g = data[i + 1]
      const b = data[i + 2]
      const brightness = (r + g + b) / 3
      
      if (brightness > 235 && r > 220 && g > 220 && b > 220) {
        data[i + 3] = 0
      } else if (brightness > 205 && r > 195 && g > 195 && b > 195) {
        const factor = 1 - (brightness - 205) / (235 - 205)
        data[i + 3] = Math.round(data[i + 3] * factor)
      }
    }
    
    ctx.putImageData(imgData, 0, 0)
    monogramUrl.value = canvas.toDataURL('image/png')
  }
}

onMounted(() => {
  processTransparentImage(rawMonogramUrl)
})

function triggerConfetti() {
  try {
    // Magical center celestial burst
    confetti({
      particleCount: 160,
      spread: 120,
      origin: { y: 0.45, x: 0.5 },
      colors: ['#ffffff', '#93c5fd', '#d4af37', '#60a5fa', '#fef08a'],
      disableForReducedMotion: true,
      gravity: 0.6,
      scalar: 1.1,
      ticks: 120,
      startVelocity: 40
    })
  } catch (e) {
    // Ignore if not loaded
  }
}

function handleOpenInvitation() {
  if (isOpening.value) return
  isOpening.value = true
  
  // Trigger magical celestial burst
  setTimeout(() => {
    triggerConfetti()
  }, 100)

  // Emit open-invitation right during the sunburst peak for a seamless cross-dissolve
  setTimeout(() => {
    emit('open-invitation')
    setTimeout(() => {
      isOpening.value = false
    }, 600)
  }, 650)
}
</script>

<style scoped>
.wedding-card-container {
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
}

.wedding-card {
  position: relative;
  width: 100%;
  height: 100%;
  max-height: 100%;
  border-radius: 0;
  overflow: hidden;
  box-shadow: none;
  background-color: #f0f9ff;
  display: flex;
  flex-direction: column;
}

/* Background Layer */
.card-bg-layer {
  position: absolute;
  inset: 0;
  z-index: 1;
}

.card-bg-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  display: block;
}

.card-lighting-overlay {
  position: absolute;
  inset: 0;
  background: radial-gradient(
    ellipse at 50% 40%,
    rgba(255, 255, 255, 0.35) 0%,
    rgba(240, 249, 255, 0.05) 60%,
    rgba(15, 23, 42, 0.08) 100%
  );
  pointer-events: none;
}

/* Content Layout */
.card-content {
  position: relative;
  z-index: 20;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 100%;
  width: 100%;
  padding: 3.5vh 20px 1.5vh 20px;
  text-align: center;
  box-sizing: border-box;
}

/* Luxurious dispersion animation for opening invitation */
.card-content > * {
  transition: transform 0.65s cubic-bezier(0.4, 0, 0.2, 1), opacity 0.55s cubic-bezier(0.4, 0, 0.2, 1), filter 0.55s ease;
  will-change: transform, opacity, filter;
}

.card-content.is-opening .monogram-section,
.card-content.is-opening .titles-section {
  opacity: 0;
  transform: translateY(-60px) scale(0.9);
  filter: blur(6px);
  pointer-events: none;
}

.card-content.is-opening .guest-section,
.card-content.is-opening .button-section {
  opacity: 0;
  transform: translateY(50px) scale(0.9);
  filter: blur(6px);
  pointer-events: none;
}


/* Celestial Sunburst Overlay matching video */
.celestial-burst-overlay {
  position: absolute;
  inset: 0;
  z-index: 25;
  display: flex;
  align-items: center;
  justify-content: center;
  pointer-events: none;
}

.sunburst-core {
  position: absolute;
  top: 32%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 200px;
  height: 200px;
  border-radius: 50%;
  background: radial-gradient(
    circle,
    rgba(255, 255, 255, 1) 0%,
    rgba(224, 242, 254, 0.95) 25%,
    rgba(96, 165, 250, 0.7) 50%,
    rgba(37, 99, 235, 0.25) 75%,
    transparent 100%
  );
  filter: blur(8px);
  animation: burstExpand 0.95s cubic-bezier(0.1, 0.9, 0.2, 1) forwards;
}

.sunburst-ring {
  position: absolute;
  top: 32%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 260px;
  height: 260px;
  border-radius: 50%;
  border: 3px solid rgba(255, 255, 255, 0.85);
  box-shadow: 0 0 35px rgba(147, 197, 253, 0.9), inset 0 0 25px rgba(255, 255, 255, 0.8);
  animation: ringExpand 0.9s cubic-bezier(0.1, 0.8, 0.25, 1) forwards;
}

.sunburst-rays {
  position: absolute;
  top: 32%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 380px;
  height: 380px;
  background: conic-gradient(
    from 0deg,
    rgba(255, 255, 255, 0.6) 0deg,
    transparent 20deg,
    rgba(147, 197, 253, 0.5) 45deg,
    transparent 65deg,
    rgba(255, 255, 255, 0.7) 90deg,
    transparent 110deg,
    rgba(147, 197, 253, 0.5) 135deg,
    transparent 155deg,
    rgba(255, 255, 255, 0.6) 180deg,
    transparent 200deg,
    rgba(147, 197, 253, 0.5) 225deg,
    transparent 245deg,
    rgba(255, 255, 255, 0.7) 270deg,
    transparent 290deg,
    rgba(147, 197, 253, 0.5) 315deg,
    transparent 335deg,
    rgba(255, 255, 255, 0.6) 360deg
  );
  border-radius: 50%;
  filter: blur(10px);
  animation: raysSpin 1.1s cubic-bezier(0.1, 0.8, 0.25, 1) forwards;
}

.diamond-stars-field {
  position: absolute;
  top: 32%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 320px;
  height: 320px;
}

.star-point {
  position: absolute;
  width: 14px;
  height: 14px;
  background: #ffffff;
  clip-path: polygon(50% 0%, 62% 38%, 100% 50%, 62% 62%, 50% 100%, 38% 62%, 0% 50%, 38% 38%);
  filter: drop-shadow(0 0 8px rgba(255, 255, 255, 1)) drop-shadow(0 0 16px rgba(96, 165, 250, 0.8));
  animation: starRadiate 0.9s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

.star-1 { top: 20%; left: 25%; animation-delay: 0.05s; }
.star-2 { top: 15%; left: 70%; animation-delay: 0.1s; transform: scale(1.3); }
.star-3 { top: 60%; left: 18%; animation-delay: 0.08s; }
.star-4 { top: 75%; left: 65%; animation-delay: 0.12s; transform: scale(1.2); }
.star-5 { top: 35%; left: 10%; animation-delay: 0.15s; }
.star-6 { top: 40%; left: 85%; animation-delay: 0.07s; transform: scale(1.4); }
.star-7 { top: 10%; left: 45%; animation-delay: 0.11s; }
.star-8 { top: 80%; left: 40%; animation-delay: 0.13s; }
.star-9 { top: 28%; left: 80%; animation-delay: 0.09s; }
.star-10 { top: 65%; left: 80%; animation-delay: 0.14s; }
.star-11 { top: 70%; left: 30%; animation-delay: 0.06s; }
.star-12 { top: 18%; left: 55%; animation-delay: 0.16s; transform: scale(1.1); }

@keyframes burstExpand {
  0% {
    transform: translate(-50%, -50%) scale(0.1);
    opacity: 0;
  }
  30% {
    opacity: 1;
  }
  80% {
    transform: translate(-50%, -50%) scale(2.6);
    opacity: 0.95;
  }
  100% {
    transform: translate(-50%, -50%) scale(3.4);
    opacity: 0;
  }
}

@keyframes ringExpand {
  0% {
    transform: translate(-50%, -50%) scale(0.2);
    opacity: 0;
  }
  30% {
    opacity: 1;
  }
  100% {
    transform: translate(-50%, -50%) scale(2.2);
    opacity: 0;
  }
}

@keyframes raysSpin {
  0% {
    transform: translate(-50%, -50%) rotate(0deg) scale(0.2);
    opacity: 0;
  }
  40% {
    opacity: 0.9;
  }
  100% {
    transform: translate(-50%, -50%) rotate(90deg) scale(2.8);
    opacity: 0;
  }
}

@keyframes starRadiate {
  0% {
    transform: scale(0.2);
    opacity: 0;
  }
  40% {
    transform: scale(1.4);
    opacity: 1;
  }
  100% {
    transform: scale(0.6) translateY(-20px);
    opacity: 0;
  }
}


/* Monogram Section (Directly on sky) */
.monogram-section {
  position: relative;
  margin-top: 4%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.monogram-ambient-glow {
  position: absolute;
  width: 160px;
  height: 160px;
  background: radial-gradient(circle, rgba(147, 197, 253, 0.6) 0%, rgba(37, 99, 235, 0.25) 50%, transparent 75%);
  filter: blur(14px);
  animation: pulseGlow 4s ease-in-out infinite;
  pointer-events: none;
}

.monogram-wrapper {
  position: relative;
  width: 135px;
  height: 135px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.monogram-pure-img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  filter: drop-shadow(0 6px 12px rgba(15, 35, 80, 0.45));
  transition: transform 0.4s ease;
}

.monogram-wrapper:hover .monogram-pure-img {
  transform: scale(1.05);
}

.monogram-shimmer {
  position: absolute;
  top: 0;
  left: -150%;
  width: 70%;
  height: 100%;
  background: linear-gradient(
    90deg,
    transparent 0%,
    rgba(255, 255, 255, 0.5) 50%,
    transparent 100%
  );
  transform: skewX(-25deg);
  animation: shimmerSweep 4.5s infinite;
  pointer-events: none;
}

@keyframes shimmerSweep {
  0% { left: -150%; }
  30%, 100% { left: 200%; }
}

/* Titles Section (Positioned down at the red line in the open bright sky) */
.titles-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  margin-top: 4.5vh;
  padding: 0 16px;
}

.main-title {
  font-family: var(--font-moul);
  font-size: 1.58rem;
  font-weight: 400;
  line-height: 1.45;
  color: #0e306e;
  background: linear-gradient(180deg, #0a2350 0%, #164696 45%, #2563eb 75%, #0e306e 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: 
    drop-shadow(0 1px 0 #ffffff)
    drop-shadow(0 -0.8px 0 rgba(255, 255, 255, 0.9))
    drop-shadow(0.8px 0 0 rgba(255, 255, 255, 0.8))
    drop-shadow(-0.8px 0 0 rgba(255, 255, 255, 0.8))
    drop-shadow(0 4px 10px rgba(10, 35, 80, 0.45));
  letter-spacing: 0.5px;
  transform: translateZ(0);
}

.sub-title {
  font-family: var(--font-moul);
  font-size: 1.18rem;
  font-weight: 400;
  line-height: 1.45;
  color: #11387e;
  background: linear-gradient(180deg, #0c2b60 0%, #1b4ea5 55%, #2563eb 85%, #0f326e 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: 
    drop-shadow(0 1px 0 #ffffff)
    drop-shadow(0 3px 6px rgba(10, 35, 80, 0.38));
  letter-spacing: 0.3px;
  transform: translateZ(0);
}

.center-spacer {
  flex: 1;
  min-height: 24px;
}

/* Guest Section (matching photo 2) */
.guest-section {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 3px;
  margin-bottom: 8px;
}

.guest-label {
  font-family: 'Kantumruy Pro', var(--font-body);
  font-size: 1.08rem;
  font-weight: 700;
  color: #0a2249;
  letter-spacing: 0.5px;
  text-shadow: 0 1px 3px rgba(255, 255, 255, 0.9);
}

.guest-underline-area {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 75%;
  max-width: 260px;
}

.guest-name {
  font-family: 'Kantumruy Pro', var(--font-body);
  font-size: 0.92rem;
  font-weight: 600;
  color: #1e3a8a;
  padding: 1px 6px;
  text-shadow: 0 1px 2px rgba(255, 255, 255, 0.9);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 100%;
}

.guest-line {
  width: 100%;
  height: 1.5px;
  background: linear-gradient(90deg, transparent 0%, rgba(13, 40, 86, 0.7) 30%, rgba(13, 40, 86, 0.7) 70%, transparent 100%);
  margin-top: 2px;
}

/* Vintage Cartouche Button (Positioned down into bottom flower bed) */
.button-section {
  width: 100%;
  display: flex;
  justify-content: center;
  margin-bottom: 2vh;
  z-index: 30;
}

.open-invitation-btn {
  position: relative;
  width: 82%;
  max-width: 275px;
  padding: 5px 6px;
  background: #f8f6f0;
  border: 1.5px solid #6c5a4b;
  border-radius: 28px;
  box-shadow: 
    0 6px 18px rgba(15, 23, 42, 0.25),
    0 1px 3px rgba(0, 0, 0, 0.12),
    inset 0 1px 0 rgba(255, 255, 255, 0.95);
  cursor: pointer;
  outline: none;
  overflow: visible;
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  animation: pulseCartouche 3.5s infinite;
}

.open-invitation-btn:hover {
  transform: translateY(-2px) scale(1.03);
  border-color: #3b82f6;
  box-shadow: 
    0 10px 25px rgba(37, 99, 235, 0.35),
    0 2px 8px rgba(0, 0, 0, 0.2);
}

.open-invitation-btn:active {
  transform: translateY(1px) scale(0.98);
}

/* Vintage Ears / Tabs on Button Sides */
.btn-ear {
  position: absolute;
  top: 50%;
  width: 10px;
  height: 10px;
  background: #f8f6f0;
  border: 1.5px solid #6c5a4b;
  transform: translateY(-50%) rotate(45deg);
  border-radius: 2px;
  z-index: 1;
}

.left-ear {
  left: -5px;
  border-right: none;
  border-top: none;
}

.right-ear {
  right: -5px;
  border-left: none;
  border-bottom: none;
}

.btn-inner-border {
  position: relative;
  z-index: 2;
  border: 1px solid rgba(108, 90, 75, 0.4);
  border-radius: 22px;
  padding: 6px 14px 5px 14px;
  background: linear-gradient(180deg, #ffffff 0%, #f7f4ed 100%);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.btn-text-km {
  font-family: 'Kantumruy Pro', var(--font-body);
  font-size: 1.05rem;
  font-weight: 700;
  color: #0c2448;
  line-height: 1.35;
  letter-spacing: 0.3px;
  text-shadow: 0 1px 1px rgba(255, 255, 255, 0.8);
}

.btn-text-en {
  font-family: 'Cinzel', 'Playfair Display', serif;
  font-size: 0.62rem;
  font-weight: 600;
  color: #574d44;
  letter-spacing: 0.8px;
  text-transform: capitalize;
  margin-top: 1px;
}

.btn-shine {
  position: absolute;
  top: -50%;
  left: -100%;
  width: 50%;
  height: 200%;
  background: linear-gradient(
    90deg,
    transparent 0%,
    rgba(255, 255, 255, 0.7) 50%,
    transparent 100%
  );
  transform: skewX(-20deg);
  animation: btnSweep 4s infinite;
  pointer-events: none;
}

@keyframes btnSweep {
  0% { left: -100%; }
  25%, 100% { left: 200%; }
}

@keyframes pulseCartouche {
  0%, 100% {
    box-shadow: 
      0 6px 18px rgba(15, 23, 42, 0.25),
      0 0 0 0 rgba(37, 99, 235, 0.3);
  }
  50% {
    box-shadow: 
      0 8px 22px rgba(37, 99, 235, 0.38),
      0 0 0 6px rgba(37, 99, 235, 0.12);
  }
}

.bottom-buffer {
  display: none;
}

/* Responsive adjustments */
@media (max-height: 700px) {
  .monogram-wrapper {
    width: 105px;
    height: 105px;
  }
  .main-title {
    font-size: 1.35rem;
  }
  .sub-title {
    font-size: 1.02rem;
  }
  .btn-text-km {
    font-size: 0.95rem;
  }
}

@media (min-width: 480px) and (min-height: 800px) {
  .main-title {
    font-size: 1.68rem;
  }
  .sub-title {
    font-size: 1.22rem;
  }
  .monogram-wrapper {
    width: 145px;
    height: 145px;
  }
}
</style>
