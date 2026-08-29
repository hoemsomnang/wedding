<template>
  <div class="music-player-wrapper">
    <button
      class="music-btn"
      :class="{ 'is-playing': isPlaying }"
      @click="toggleMusic"
      :title="isPlaying ? 'Pause Music (បិទតន្ត្រី)' : 'Play Music (បើកតន្ត្រី)'"
      aria-label="Toggle Background Music"
    >
      <div class="disc-glow"></div>
      <div class="disc-body">
        <div class="disc-grooves"></div>
        <div class="disc-center">
          <svg v-if="isPlaying" class="music-icon" viewBox="0 0 24 24" width="18" height="18" fill="currentColor">
            <path d="M12 3v10.55c-.59-.34-1.27-.55-2-.55-2.21 0-4 1.79-4 4s1.79 4 4 4 4-1.79 4-4V7h4V3h-6z"/>
          </svg>
          <svg v-else class="music-icon paused" viewBox="0 0 24 24" width="18" height="18" fill="currentColor">
            <path d="M4.27 3L3 4.27l9 9v.28c-.59-.34-1.27-.55-2-.55-2.21 0-4 1.79-4 4s1.79 4 4 4 4-1.79 4-4v-1.73l4.27 4.27 1.27-1.27L4.27 3zM14 7h4V3h-6v5.18l2 2V7z"/>
          </svg>
        </div>
      </div>

      <!-- Animated equalizer bars when playing -->
      <div v-if="isPlaying" class="sound-wave">
        <span class="bar bar-1"></span>
        <span class="bar bar-2"></span>
        <span class="bar bar-3"></span>
        <span class="bar bar-4"></span>
      </div>
    </button>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isPlaying = ref(false)
let audioCtx = null
let melodyTimer = null
let noteIndex = 0

// Romantic Wedding Canon / Arpeggio Chords in D/F Major
const weddingNotes = [
  // F Major / C / Dm / Bb romantic progression notes in Hz
  349.23, 440.00, 523.25, 698.46, // F4, A4, C5, F5
  261.63, 329.63, 392.00, 523.25, // C4, E4, G4, C5
  293.66, 349.23, 440.00, 587.33, // D4, F4, A4, D5
  233.08, 293.66, 349.23, 466.16, // Bb3, D4, F4, Bb4
  349.23, 440.00, 523.25, 698.46, 
  392.00, 493.88, 587.33, 783.99, // G4, B4, D5, G5
  523.25, 659.25, 783.99, 1046.50 // C5, E5, G5, C6
]

const bassNotes = [
  174.61, 130.81, 146.83, 116.54, 174.61, 196.00, 261.63
]

function playRomanticNote(freq, type = 'sine', duration = 1.2, gainValue = 0.08) {
  if (!audioCtx || audioCtx.state !== 'running') return
  try {
    const osc = audioCtx.createOscillator()
    const gain = audioCtx.createGain()
    const filter = audioCtx.createBiquadFilter()

    osc.type = type
    osc.frequency.setValueAtTime(freq, audioCtx.currentTime)

    // Soft lowpass filter for gentle warm harp/music box timbre
    filter.type = 'lowpass'
    filter.frequency.setValueAtTime(1400, audioCtx.currentTime)

    gain.gain.setValueAtTime(0.001, audioCtx.currentTime)
    gain.gain.exponentialRampToValueAtTime(gainValue, audioCtx.currentTime + 0.08)
    gain.gain.exponentialRampToValueAtTime(0.0001, audioCtx.currentTime + duration)

    osc.connect(filter)
    filter.connect(gain)
    gain.connect(audioCtx.destination)

    osc.start()
    osc.stop(audioCtx.currentTime + duration)
  } catch (e) {
    console.error('Audio play error', e)
  }
}

function startMelodyLoop() {
  if (melodyTimer) clearInterval(melodyTimer)
  
  melodyTimer = setInterval(() => {
    if (!isPlaying.value) return
    const freq = weddingNotes[noteIndex % weddingNotes.length]
    
    // Play main bell/harp note
    playRomanticNote(freq, 'sine', 1.8, 0.09)
    
    // Play warm shimmer overtone
    if (noteIndex % 2 === 0) {
      playRomanticNote(freq * 1.5, 'triangle', 1.2, 0.03)
    }

    // Play bass note every 4 beats
    if (noteIndex % 4 === 0) {
      const bassFreq = bassNotes[(noteIndex / 4) % bassNotes.length]
      playRomanticNote(bassFreq, 'sine', 2.5, 0.06)
    }

    noteIndex++
  }, 480)
}

function toggleMusic() {
  if (!audioCtx) {
    const AudioContextClass = window.AudioContext || window.webkitAudioContext
    if (AudioContextClass) {
      audioCtx = new AudioContextClass()
    }
  }

  if (audioCtx && audioCtx.state === 'suspended') {
    audioCtx.resume()
  }

  isPlaying.value = !isPlaying.value

  if (isPlaying.value) {
    startMelodyLoop()
  } else {
    if (melodyTimer) clearInterval(melodyTimer)
  }
}

// Auto enable on first user interaction if preferred
const startOnFirstInteraction = () => {
  if (!isPlaying.value && !audioCtx) {
    // Keep ready
  }
}

onMounted(() => {
  window.addEventListener('click', startOnFirstInteraction, { once: true })
})

onUnmounted(() => {
  if (melodyTimer) clearInterval(melodyTimer)
  if (audioCtx) audioCtx.close()
})

defineExpose({
  toggleMusic,
  isPlaying
})
</script>

<style scoped>
.music-player-wrapper {
  position: fixed;
  top: 20px;
  right: 20px;
  z-index: 99;
}

.music-btn {
  position: relative;
  width: 46px;
  height: 46px;
  border-radius: 50%;
  background: rgba(15, 23, 42, 0.75);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border: 1.5px solid rgba(212, 175, 55, 0.6);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3), 0 0 12px rgba(37, 99, 235, 0.3);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  outline: none;
}

.music-btn:hover {
  transform: scale(1.08);
  border-color: rgba(212, 175, 55, 1);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.4), 0 0 20px rgba(37, 99, 235, 0.6);
}

.disc-glow {
  position: absolute;
  inset: -3px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(37, 99, 235, 0.4), transparent 70%);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.is-playing .disc-glow {
  opacity: 1;
  animation: pulseGlow 2.5s infinite;
}

.disc-body {
  position: relative;
  width: 38px;
  height: 38px;
  border-radius: 50%;
  background: radial-gradient(circle, #1e293b 30%, #0f172a 90%);
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid rgba(255, 255, 255, 0.15);
}

.is-playing .disc-body {
  animation: spinDisc 6s linear infinite;
}

.disc-grooves {
  position: absolute;
  inset: 4px;
  border-radius: 50%;
  border: 1px dashed rgba(255, 255, 255, 0.15);
}

.disc-center {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: linear-gradient(135deg, #1e40af, #3b82f6);
  display: flex;
  align-items: center;
  justify-content: center;
  color: #ffffff;
  box-shadow: inset 0 0 4px rgba(0, 0, 0, 0.5);
}

.music-icon {
  width: 12px;
  height: 12px;
}

.music-icon.paused {
  color: #94a3b8;
}

/* Equalizer Bars */
.sound-wave {
  position: absolute;
  bottom: -6px;
  display: flex;
  align-items: flex-end;
  gap: 2px;
  height: 10px;
  padding: 0 4px;
  background: rgba(15, 23, 42, 0.85);
  border-radius: 4px;
  border: 0.5px solid rgba(212, 175, 55, 0.5);
}

.bar {
  width: 2px;
  background: #60a5fa;
  border-radius: 1px;
}

.bar-1 { height: 4px; animation: bounce 0.6s ease infinite alternate; }
.bar-2 { height: 8px; animation: bounce 0.8s ease infinite alternate 0.2s; }
.bar-3 { height: 6px; animation: bounce 0.5s ease infinite alternate 0.4s; }
.bar-4 { height: 5px; animation: bounce 0.7s ease infinite alternate 0.1s; }

@keyframes spinDisc {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes bounce {
  0% { height: 2px; background: #60a5fa; }
  100% { height: 10px; background: #93c5fd; }
}

@media (max-width: 480px) {
  .music-player-wrapper {
    top: 15px;
    right: 15px;
  }
}
</style>
