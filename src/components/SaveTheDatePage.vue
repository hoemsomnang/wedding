<template>
  <div class="invitation-page-container">
    <!-- Main Card Frame -->
    <div class="invitation-card">
      
      <!-- Background Layer matching Photo 1 -->
      <div class="card-bg-layer">
        <img
          :src="invitationBgUrl"
          alt="Wedding Floral Background"
          class="card-bg-img"
        />
        <div class="bg-gradient-overlay"></div>
      </div>

      <!-- Subtle Floating Petals & Sparkle Atmosphere -->
      <ParticleEffects />

      <!-- Top Right Floating Audio Toggle Button -->
      <div class="top-audio-bar">
        <button
          class="sound-toggle-btn"
          :class="{ active: isPlaying }"
          @click="toggleMusic"
          aria-label="បិទ/បើកតន្ត្រី (Music Toggle)"
          title="Toggle Music"
        >
          <svg v-if="isPlaying" viewBox="0 0 24 24" width="20" height="20" fill="currentColor">
            <path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/>
          </svg>
          <svg v-else viewBox="0 0 24 24" width="20" height="20" fill="currentColor">
            <path d="M16.5 12c0-1.77-1.02-3.29-2.5-4.03v2.21l2.45 2.45c.03-.2.05-.41.05-.63zm2.5 0c0 .94-.2 1.82-.54 2.64l1.51 1.51C20.63 14.91 21 13.5 21 12c0-4.28-2.99-7.86-7-8.77v2.06c2.89.86 5 3.54 5 6.71zM4.27 3L3 4.27l4.73 4.73H3v6h4l5 5v-6.73l4.25 4.25c-.67.52-1.42.93-2.25 1.18v2.06c1.38-.31 2.63-.95 3.69-1.81L19.73 21 21 19.73l-9-9L4.27 3zM12 4L9.91 6.09 12 8.18V4z"/>
          </svg>
        </button>
      </div>

      <!-- Main Invitation Typography Area (Matching Photo 2) -->
      <div class="invitation-body-scroll">
        <div class="invitation-content">
          
          <!-- Monogram Crest -->
          <div class="monogram-section">
            <img
              :src="monogramUrl"
              alt="Monogram Crest M"
              class="monogram-img"
            />
          </div>

          <!-- Main Wedding Ceremony Title -->
          <h1 class="main-wedding-title">សិរីមង្គលអាពាហ៍ពិពាហ៍</h1>

          <!-- Parents Section (2 Columns) -->
          <div class="parents-grid">
            <div class="parent-col left-col">
              <div class="parent-row">
                <span class="role-text">លោក</span>
                <span class="name-text">ប៉ែនសេង ខេម រ៉ូហ្វង់</span>
              </div>
              <div class="parent-row">
                <span class="role-text">លោកស្រី</span>
                <span class="name-text">ចាន់ធី ម៉ារី យ៉ង់</span>
              </div>
            </div>

            <div class="parent-col right-col">
              <div class="parent-row">
                <span class="role-text">លោក</span>
                <span class="name-text">ស៊ូ ចំរើន</span>
              </div>
              <div class="parent-row">
                <span class="role-text">លោកស្រី</span>
                <span class="name-text">ឌុច យ៉ែម</span>
              </div>
            </div>
          </div>

          <!-- Invitation Subtitle -->
          <div class="honor-invite-title">
            មានកិត្តិយសសូមគោរពអញ្ជើញ
          </div>

          <!-- Formal Invitation Body Text -->
          <div class="formal-invitation-text">
            <p>ឯកឧត្តម លោកជំទាវ អ្នកឧកញ៉ា ឧកញ៉ា លោក លោកស្រី អ្នកនាង កញ្ញា</p>
            <p>អញ្ជើញចូលរួមជាអធិបតី និងភ្ញៀវកិត្តិយស ដើម្បីប្រសិទ្ធពរជ័យ សិរីសួស្តីជ័យមង្គលក្នុង</p>
            <p>ពិធីសិរីមង្គលអាពាហ៍ពិពាហ៍កូនប្រុស កូនស្រីរបស់យើងខ្ញុំ</p>
          </div>

          <!-- Groom & Bride Names (2 Columns) -->
          <div class="couple-names-grid">
            <div class="couple-col groom-col">
              <span class="couple-role">កូនប្រុសនាម</span>
              <h2 class="couple-name">ម៉ាត ផេង ឡុញហ័រ</h2>
            </div>
            <div class="couple-col bride-col">
              <span class="couple-role">កូនស្រីនាម</span>
              <h2 class="couple-name">ធីតា រ៉េន ឡុញហ័រ</h2>
            </div>
          </div>

          <!-- Wedding Auspicious Date & Time -->
          <div class="wedding-datetime-section">
            <p class="khmer-lunar-date">នៅថ្ងៃសុក្រ ៥កើត ខែចេត្រ ឆ្នាំរោង ឆស័ក ពុទ្ធសករាជ ២៥៦៨</p>
            <p class="solar-date-highlight">ត្រូវនឹងថ្ងៃទី ២៧ ខែមីនា ឆ្នាំ ២០២៦</p>
            <p class="reception-time">វេលាម៉ោង ០៥ : ០០ ល្ងាចនៅ</p>
          </div>

          <!-- Wedding Reception Venue -->
          <div class="venue-section">
            <h3 class="venue-main-name">ភោជនីយដ្ឋាន សេនជូរីប្រាយ</h3>
            <p class="venue-address-line">ផ្ទះលេខ ១០២ ផ្លូវលេខ ៣១៥</p>
            <p class="venue-address-line">សង្កាត់បឹងកក់២ ខណ្ឌទួលគោក រាជធានីភ្នំពេញ</p>
            <p class="venue-closing-wish">ដោយមេត្រីភាព។</p>
          </div>

          <!-- Chevron Up Indicator -->
          <div class="up-indicator-wrap">
            <ChevronUp :size="24" stroke-width="2.5" class="bounce-up-icon" />
          </div>

          <!-- Bottom Spacer to let bottom navigation breathe -->
          <div class="bottom-spacer"></div>

        </div>
      </div>

      <!-- Bottom Floating 4-Button Navigation Bar (Matching Photo 2) -->
      <div class="bottom-action-nav">
        <button class="nav-action-btn" @click="openModal('calendar')" title="កាលបរិច្ឆេទ (Date & Countdown)">
          <CalendarDays :size="22" stroke-width="1.8" />
        </button>
        <button class="nav-action-btn" @click="openModal('location')" title="ទីតាំង (Map & Location)">
          <MapPin :size="22" stroke-width="1.8" />
        </button>
        <button class="nav-action-btn" @click="openModal('gallery')" title="កម្រងរូបភាព (Photo Gallery)">
          <Image :size="22" stroke-width="1.8" />
        </button>
        <button class="nav-action-btn" @click="openModal('rsvp')" title="ជូនពរ & RSVP (Blessing & Wish)">
          <MessageCircle :size="22" stroke-width="1.8" />
        </button>
      </div>

    </div>

    <!-- MODALS for Bottom Action Buttons -->
    
    <!-- 1. Calendar & Countdown Modal -->
    <div v-if="activeModal === 'calendar'" class="modal-backdrop" @click.self="closeModal">
      <div class="modal-card">
        <div class="modal-header">
          <h3 class="modal-title">កាលបរិច្ឆេទ & រាប់ថយក្រោយ</h3>
          <button class="close-btn" @click="closeModal">&times;</button>
        </div>
        <div class="modal-body">
          <div class="countdown-badge">
            <span class="badge-title">ថ្ងៃសិរីមង្គលអាពាហ៍ពិពាហ៍</span>
            <span class="badge-date">ថ្ងៃសុក្រ ទី២៧ ខែមីនា ឆ្នាំ២០២៦</span>
          </div>

          <div class="countdown-grid">
            <div class="time-box">
              <span class="time-val">{{ countdown.days }}</span>
              <span class="time-lbl">ថ្ងៃ</span>
            </div>
            <span class="time-sep">:</span>
            <div class="time-box">
              <span class="time-val">{{ countdown.hours }}</span>
              <span class="time-lbl">ម៉ោង</span>
            </div>
            <span class="time-sep">:</span>
            <div class="time-box">
              <span class="time-val">{{ countdown.minutes }}</span>
              <span class="time-lbl">នាទី</span>
            </div>
            <span class="time-sep">:</span>
            <div class="time-box">
              <span class="time-val">{{ countdown.seconds }}</span>
              <span class="time-lbl">វិនាទី</span>
            </div>
          </div>

          <a
            href="https://calendar.google.com/calendar/render?action=TEMPLATE&text=Wedding+Ceremony&dates=20260327T100000Z/20260327T150000Z&details=Wedding+Invitation&location=Century+Bright+Restaurant+Phnom+Penh"
            target="_blank"
            rel="noopener noreferrer"
            class="action-link-btn"
          >
            <CalendarDays :size="18" /> បន្ថែមទៅក្នុងប្រតិទិន (Add to Calendar)
          </a>
        </div>
      </div>
    </div>

    <!-- 2. Location & Map Modal -->
    <div v-if="activeModal === 'location'" class="modal-backdrop" @click.self="closeModal">
      <div class="modal-card">
        <div class="modal-header">
          <h3 class="modal-title">ទីតាំងពិធីមង្គលការ</h3>
          <button class="close-btn" @click="closeModal">&times;</button>
        </div>
        <div class="modal-body">
          <h4 class="location-venue-name">ភោជនីយដ្ឋាន សេនជូរីប្រាយ</h4>
          <p class="location-address">ផ្ទះលេខ ១០២ ផ្លូវលេខ ៣១៥ សង្កាត់បឹងកក់២ ខណ្ឌទួលគោក រាជធានីភ្នំពេញ</p>
          
          <div class="map-preview-box">
            <iframe
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3908.7707440333215!2d104.89679117585093!3d11.568285944062085!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x31095176046e7ab9%3A0xbb1df93d3957252!2sCentury%20Bright%20Restaurant!5e0!3m2!1sen!2skh!4v1700000000000!5m2!1sen!2skh"
              width="100%"
              height="200"
              style="border:0; border-radius: 12px;"
              allowfullscreen=""
              loading="lazy"
              referrerpolicy="no-referrer-when-downgrade"
            ></iframe>
          </div>

          <a
            href="https://maps.google.com/?q=Century+Bright+Restaurant+Phnom+Penh"
            target="_blank"
            rel="noopener noreferrer"
            class="action-link-btn"
          >
            <MapPin :size="18" /> បើកមើលក្នុង Google Maps
          </a>
        </div>
      </div>
    </div>

    <!-- 3. Photo Gallery Modal -->
    <div v-if="activeModal === 'gallery'" class="modal-backdrop" @click.self="closeModal">
      <div class="modal-card gallery-modal-card">
        <div class="modal-header">
          <h3 class="modal-title">កម្រងរូបភាពអនុស្សាវរីយ៍</h3>
          <button class="close-btn" @click="closeModal">&times;</button>
        </div>
        <div class="modal-body gallery-body">
          <div class="gallery-preview-grid">
            <div class="gallery-item-placeholder" v-for="n in 4" :key="'photo-' + n">
              <div class="photo-inner-card">
                <Image :size="32" class="photo-icon" />
                <span>រូបថតគូស្នេហ៍ {{ n }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- 4. RSVP / Wishes Modal -->
    <div v-if="activeModal === 'rsvp'" class="modal-backdrop" @click.self="closeModal">
      <div class="modal-card">
        <div class="modal-header">
          <h3 class="modal-title">ប្រសិទ្ធពរជ័យ & វត្តមាន</h3>
          <button class="close-btn" @click="closeModal">&times;</button>
        </div>
        <div class="modal-body">
          <form @submit.prevent="submitWish" class="wish-form">
            <input
              type="text"
              v-model="wishSender"
              placeholder="ឈ្មោះរបស់អ្នក (Your Name)"
              class="form-input"
              required
            />
            <textarea
              v-model="wishMessage"
              placeholder="ពាក្យជូនពរដល់គូស្វាមីភរិយាថ្មី... (Your wedding wish)"
              class="form-textarea"
              rows="3"
              required
            ></textarea>
            <button type="submit" class="action-link-btn wish-submit-btn">
              <MessageCircle :size="18" /> ផ្ញើពាក្យជូនពរ (Send Wish)
            </button>
            <p v-if="wishSent" class="wish-success-msg">✨ សូមអរគុណសម្រាប់ពាក្យជូនពរដ៏មានអត្ថន័យ!</p>
          </form>
        </div>
      </div>
    </div>

  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import ParticleEffects from './ParticleEffects.vue'
import rawMonogramUrl from '../assets/sapphire_m_crest_pure.jpg'
import invitationBgUrl from '../assets/background2.jpg'
import { CalendarDays, MapPin, Image, MessageCircle, ChevronUp } from 'lucide-vue-next'

const monogramUrl = ref(rawMonogramUrl)
const isPlaying = ref(false)
let audio = null

const activeModal = ref(null) // 'calendar' | 'location' | 'gallery' | 'rsvp' | null
const wishSender = ref('')
const wishMessage = ref('')
const wishSent = ref(false)

// Process transparent background for the monogram crest
function processTransparentImage(src) {
  const img = new window.Image()
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

// Countdown timer to 27 March 2026
const targetDate = new Date('2026-03-27T17:00:00')
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
      days: String(days).padStart(2, '0'),
      hours: String(hours).padStart(2, '0'),
      minutes: String(minutes).padStart(2, '0'),
      seconds: String(seconds).padStart(2, '0')
    }
  }
}

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
    }).catch(e => console.log('Audio playback prevented:', e))
  }
}

function openModal(modalName) {
  activeModal.value = modalName
  wishSent.value = false
}

function closeModal() {
  activeModal.value = null
}

function submitWish() {
  if (wishSender.value.trim() && wishMessage.value.trim()) {
    wishSent.value = true
    setTimeout(() => {
      wishSender.value = ''
      wishMessage.value = ''
    }, 2000)
  }
}

onMounted(() => {
  processTransparentImage(rawMonogramUrl)
  updateCountdown()
  timer = setInterval(updateCountdown, 1000)
})

onUnmounted(() => {
  if (timer) clearInterval(timer)
  if (audio) audio.pause()
})
</script>

<style lang="scss" scoped>
$sapphire-dark: #1e3a5f;
$sapphire-navy: #15325b;
$sapphire-blue: #2563eb;
$khmer-title-font: 'Moul', 'Bayon', 'Koulen', serif;
$khmer-body-font: 'Kantumruy Pro', 'Battambang', sans-serif;

.invitation-page-container {
  width: 100vw;
  height: 100vh;
  height: 100dvh;
  max-width: 100%;
  padding: 0;
  margin: 0;
  overflow: hidden;
  position: relative;
  background-color: #0b132b;
  display: flex;
  justify-content: center;
  align-items: center;
}

.invitation-card {
  position: relative;
  width: 100%;
  max-width: 480px;
  height: 100%;
  max-height: 100vh;
  max-height: 100dvh;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  box-shadow: 0 0 40px rgba(0, 0, 0, 0.4);
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

.bg-gradient-overlay {
  position: absolute;
  inset: 0;
  background: radial-gradient(
    ellipse at 50% 50%,
    rgba(255, 255, 255, 0.35) 0%,
    rgba(240, 248, 255, 0.15) 60%,
    rgba(147, 197, 253, 0.05) 100%
  );
  pointer-events: none;
}

/* Top Audio Bar */
.top-audio-bar {
  position: absolute;
  top: 14px;
  right: 14px;
  z-index: 30;
}

.sound-toggle-btn {
  width: 38px;
  height: 38px;
  border-radius: 12px;
  background: rgba(255, 255, 255, 0.75);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  border: 1px solid rgba(255, 255, 255, 0.9);
  color: $sapphire-navy;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 12px rgba(15, 23, 42, 0.12);
  cursor: pointer;
  transition: all 0.25s ease;

  &:hover {
    transform: scale(1.06);
    background: rgba(255, 255, 255, 0.95);
  }

  &.active {
    background: linear-gradient(135deg, #1d4ed8 0%, #0e306e 100%);
    color: #ffffff;
    box-shadow: 0 4px 12px rgba(29, 78, 216, 0.35);
  }
}

/* Scrollable Content Container */
.invitation-body-scroll {
  position: relative;
  z-index: 10;
  width: 100%;
  height: 100%;
  overflow-y: auto;
  overflow-x: hidden;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  scrollbar-width: none; /* Hide scrollbar Firefox */
  -ms-overflow-style: none; /* Hide scrollbar IE */

  &::-webkit-scrollbar {
    display: none; /* Hide scrollbar Chrome/Safari */
  }
}

.invitation-content {
  width: 100%;
  max-width: 440px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 17vh 16px 20px 16px;
  box-sizing: border-box;
  text-align: center;
  margin: 0 auto;

  @media (max-height: 750px) {
    padding-top: 14vh;
  }

  @media (max-height: 650px) {
    padding-top: 12vh;
  }
}

/* Monogram Section */
.monogram-section {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 0;
  margin-bottom: 4px;
  height: 72px;

  @media (max-height: 700px) {
    height: 58px;
  }
}

.monogram-img {
  max-height: 100%;
  width: auto;
  object-fit: contain;
  filter: drop-shadow(0 4px 8px rgba(21, 50, 91, 0.25)) drop-shadow(0 0 12px rgba(255, 255, 255, 0.8));
  animation: gentleFloat 4s ease-in-out infinite alternate;
}

@keyframes gentleFloat {
  0% { transform: translateY(0); }
  100% { transform: translateY(-3px); }
}

/* Main Wedding Title */
.main-wedding-title {
  font-family: $khmer-title-font;
  font-size: 1.42rem;
  font-weight: 400;
  color: $sapphire-navy;
  margin: 2px auto 8px auto;
  text-align: center;
  width: 100%;
  letter-spacing: 0.5px;
  line-height: 1.4;
  text-shadow: 0 1px 3px rgba(255, 255, 255, 0.95), 0 0 10px rgba(255, 255, 255, 0.8);
  filter: drop-shadow(0 1px 2px rgba(255, 255, 255, 0.9));

  @media (max-width: 380px) {
    font-size: 1.26rem;
  }

  @media (max-height: 700px) {
    font-size: 1.2rem;
    margin: 2px auto 4px auto;
  }
}

/* Parents Grid (2 Columns) */
.parents-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  width: 100%;
  max-width: 390px;
  gap: 12px;
  margin: 4px auto 8px auto;
  padding: 0 4px;
  justify-content: center;

  @media (max-height: 700px) {
    margin: 2px auto 4px auto;
    gap: 8px;
  }
}

.parent-col {
  display: flex;
  flex-direction: column;
  gap: 4px;

  &.left-col {
    text-align: left;
    padding-left: 6px;
  }

  &.right-col {
    text-align: left;
    padding-left: 6px;
  }
}

.parent-row {
  display: flex;
  flex-wrap: wrap;
  align-items: baseline;
  gap: 4px;
  font-family: $khmer-body-font;
  line-height: 1.35;
  text-shadow: 0 1px 3px rgba(255, 255, 255, 0.9);
}

.role-text {
  font-size: 0.85rem;
  font-weight: 700;
  color: #1e3a5f;
  white-space: nowrap;

  @media (max-width: 380px) {
    font-size: 0.78rem;
  }
}

.name-text {
  font-size: 0.85rem;
  font-weight: 700;
  color: #1e3a5f;
  white-space: nowrap;

  @media (max-width: 380px) {
    font-size: 0.78rem;
  }
}

/* Honor Invitation Subtitle */
.honor-invite-title {
  font-family: $khmer-title-font;
  font-size: 0.96rem;
  font-weight: 400;
  color: #15325b;
  margin: 8px 0 6px 0;
  line-height: 1.4;
  text-shadow: 0 1px 3px rgba(255, 255, 255, 0.95);

  @media (max-height: 700px) {
    font-size: 0.88rem;
    margin: 4px 0 4px 0;
  }
}

/* Formal Invitation Text */
.formal-invitation-text {
  font-family: $khmer-body-font;
  font-size: 0.78rem;
  line-height: 1.45;
  color: #24416b;
  margin: 4px 0 10px 0;
  padding: 0 4px;
  font-weight: 500;
  text-shadow: 0 1px 2px rgba(255, 255, 255, 0.95);

  p {
    margin: 2px 0;
  }

  @media (max-width: 380px) {
    font-size: 0.72rem;
  }

  @media (max-height: 700px) {
    font-size: 0.7rem;
    line-height: 1.35;
    margin: 2px 0 6px 0;
  }
}

/* Couple Names Grid (2 Columns) */
.couple-names-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  width: 100%;
  gap: 16px;
  margin: 8px 0 10px 0;

  @media (max-height: 700px) {
    margin: 4px 0 6px 0;
  }
}

.couple-col {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
}

.couple-role {
  font-family: $khmer-body-font;
  font-size: 0.82rem;
  font-weight: 600;
  color: #3b5c87;

  @media (max-width: 380px) {
    font-size: 0.75rem;
  }
}

.couple-name {
  font-family: $khmer-title-font;
  font-size: 1.18rem;
  font-weight: 400;
  color: #15325b;
  margin: 0;
  line-height: 1.3;

  @media (max-width: 380px) {
    font-size: 1.05rem;
  }

  @media (max-height: 700px) {
    font-size: 1.02rem;
  }
}

/* Date & Time Section */
.wedding-datetime-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 3px;
  margin: 8px 0 10px 0;
  font-family: $khmer-body-font;

  @media (max-height: 700px) {
    margin: 4px 0 6px 0;
    gap: 2px;
  }
}

.khmer-lunar-date {
  font-size: 0.78rem;
  font-weight: 500;
  color: #24416b;
  margin: 0;

  @media (max-width: 380px) {
    font-size: 0.72rem;
  }
}

.solar-date-highlight {
  font-size: 0.95rem;
  font-weight: 700;
  color: #102a4f;
  margin: 1px 0;

  @media (max-width: 380px) {
    font-size: 0.88rem;
  }
}

.reception-time {
  font-size: 0.84rem;
  font-weight: 600;
  color: #1e3a5f;
  margin: 0;

  @media (max-width: 380px) {
    font-size: 0.76rem;
  }
}

/* Venue Section */
.venue-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
  margin: 6px 0 6px 0;
  font-family: $khmer-body-font;

  @media (max-height: 700px) {
    margin: 2px 0 4px 0;
  }
}

.venue-main-name {
  font-family: $khmer-title-font;
  font-size: 0.98rem;
  font-weight: 400;
  color: #15325b;
  margin: 0 0 2px 0;

  @media (max-width: 380px) {
    font-size: 0.9rem;
  }
}

.venue-address-line {
  font-size: 0.76rem;
  font-weight: 500;
  color: #24416b;
  margin: 0;

  @media (max-width: 380px) {
    font-size: 0.7rem;
  }
}

.venue-closing-wish {
  font-size: 0.78rem;
  font-weight: 600;
  color: #15325b;
  margin: 2px 0 0 0;
}

/* Up Arrow Indicator */
.up-indicator-wrap {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 4px;
  color: #15325b;
}

.bounce-up-icon {
  animation: bounceUp 1.8s infinite ease-in-out;
}

@keyframes bounceUp {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-5px); }
}

.bottom-spacer {
  height: 85px;
  width: 100%;
}

/* Bottom Floating Navigation (4 Glass Cards) */
.bottom-action-nav {
  position: absolute;
  bottom: 16px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 8px 14px;
  background: rgba(255, 255, 255, 0.72);
  backdrop-filter: blur(14px);
  -webkit-backdrop-filter: blur(14px);
  border: 1px solid rgba(255, 255, 255, 0.9);
  border-radius: 20px;
  box-shadow: 0 8px 24px rgba(15, 35, 70, 0.12);
  z-index: 40;
}

.nav-action-btn {
  width: 48px;
  height: 48px;
  border-radius: 14px;
  background: rgba(255, 255, 255, 0.85);
  border: 1px solid rgba(255, 255, 255, 0.95);
  display: flex;
  align-items: center;
  justify-content: center;
  color: #15325b;
  cursor: pointer;
  transition: all 0.25s cubic-bezier(0.16, 1, 0.3, 1);
  box-shadow: 0 2px 8px rgba(15, 35, 70, 0.08);

  &:hover {
    transform: translateY(-3px) scale(1.05);
    background: #ffffff;
    color: #2563eb;
    box-shadow: 0 6px 16px rgba(37, 99, 235, 0.2);
  }

  &:active {
    transform: scale(0.95);
  }
}

/* MODAL STYLES */
.modal-backdrop {
  position: fixed;
  inset: 0;
  background: rgba(11, 25, 48, 0.6);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
  animation: fadeIn 0.25s ease-out;
}

.modal-card {
  width: 100%;
  max-width: 420px;
  background: rgba(255, 255, 255, 0.96);
  border-radius: 24px;
  padding: 22px 20px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.25);
  border: 1px solid rgba(255, 255, 255, 0.8);
  animation: scaleIn 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}

.modal-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}

.modal-title {
  font-family: $khmer-title-font;
  font-size: 1.15rem;
  color: $sapphire-navy;
  margin: 0;
}

.close-btn {
  background: none;
  border: none;
  font-size: 1.6rem;
  color: #64748b;
  cursor: pointer;
  padding: 0 4px;
  line-height: 1;

  &:hover {
    color: #0f172a;
  }
}

.modal-body {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 14px;
  text-align: center;
}

.countdown-badge {
  display: flex;
  flex-direction: column;
  gap: 4px;

  .badge-title {
    font-family: $khmer-title-font;
    font-size: 0.95rem;
    color: #2563eb;
  }

  .badge-date {
    font-family: $khmer-body-font;
    font-size: 0.9rem;
    font-weight: 700;
    color: #1e293b;
  }
}

.countdown-grid {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  width: 100%;
}

.time-box {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-width: 52px;
  padding: 8px 4px;
  background: #f1f5f9;
  border-radius: 12px;
  border: 1px solid #cbd5e1;

  .time-val {
    font-family: 'Cinzel', monospace;
    font-size: 1.25rem;
    font-weight: 700;
    color: #1e3a5f;
  }

  .time-lbl {
    font-family: $khmer-body-font;
    font-size: 0.72rem;
    font-weight: 600;
    color: #64748b;
  }
}

.time-sep {
  font-family: 'Cinzel', monospace;
  font-size: 1.2rem;
  font-weight: 700;
  color: #94a3b8;
}

.action-link-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: 100%;
  padding: 12px 18px;
  border-radius: 14px;
  background: linear-gradient(135deg, #1d4ed8 0%, #1e3a8a 100%);
  color: #ffffff;
  font-family: $khmer-body-font;
  font-size: 0.92rem;
  font-weight: 600;
  text-decoration: none;
  border: none;
  cursor: pointer;
  box-shadow: 0 4px 14px rgba(29, 78, 216, 0.35);
  transition: all 0.25s ease;

  &:hover {
    background: linear-gradient(135deg, #2563eb 0%, #1d4ed8 100%);
    box-shadow: 0 6px 18px rgba(29, 78, 216, 0.45);
    transform: translateY(-1px);
  }
}

.location-venue-name {
  font-family: $khmer-title-font;
  font-size: 1.1rem;
  color: #1e3a5f;
  margin: 0;
}

.location-address {
  font-family: $khmer-body-font;
  font-size: 0.85rem;
  color: #475569;
  margin: 0;
  line-height: 1.4;
}

.map-preview-box {
  width: 100%;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.gallery-preview-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  width: 100%;
}

.gallery-item-placeholder {
  aspect-ratio: 1;
  background: #f1f5f9;
  border-radius: 14px;
  border: 1px dashed #94a3b8;
  display: flex;
  align-items: center;
  justify-content: center;
}

.photo-inner-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
  color: #64748b;
  font-family: $khmer-body-font;
  font-size: 0.78rem;
}

.wish-form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 100%;
}

.form-input, .form-textarea {
  width: 100%;
  padding: 10px 14px;
  border-radius: 12px;
  border: 1px solid #cbd5e1;
  font-family: $khmer-body-font;
  font-size: 0.88rem;
  background: #f8fafc;
  box-sizing: border-box;

  &:focus {
    outline: none;
    border-color: #2563eb;
    background: #ffffff;
    box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.15);
  }
}

.wish-success-msg {
  font-family: $khmer-body-font;
  font-size: 0.88rem;
  font-weight: 600;
  color: #059669;
  margin: 4px 0 0 0;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes scaleIn {
  from { opacity: 0; transform: scale(0.92); }
  to { opacity: 1; transform: scale(1); }
}
</style>
