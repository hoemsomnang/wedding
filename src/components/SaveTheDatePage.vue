<template>
  <div class="save-the-date-page">
    <!-- Main Card Frame Wrapper -->
    <div class="invitation-card">
      
      <!-- Background Layer (Fixed floral background) -->
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
          title="Toggle Romantic Wedding Music"
        >
          <div v-if="isPlaying" class="sound-waves-indicator">
            <span class="bar bar-1"></span>
            <span class="bar bar-2"></span>
            <span class="bar bar-3"></span>
          </div>
          <svg v-if="isPlaying" viewBox="0 0 24 24" width="18" height="18" fill="currentColor">
            <path d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z"/>
          </svg>
          <svg v-else viewBox="0 0 24 24" width="18" height="18" fill="currentColor">
            <path d="M16.5 12c0-1.77-1.02-3.29-2.5-4.03v2.21l2.45 2.45c.03-.2.05-.41.05-.63zm2.5 0c0 .94-.2 1.82-.54 2.64l1.51 1.51C20.63 14.91 21 13.5 21 12c0-4.28-2.99-7.86-7-8.77v2.06c2.89.86 5 3.54 5 6.71zM4.27 3L3 4.27l4.73 4.73H3v6h4l5 5v-6.73l4.25 4.25c-.67.52-1.42.93-2.25 1.18v2.06c1.38-.31 2.63-.95 3.69-1.81L19.73 21 21 19.73l-9-9L4.27 3zM12 4L9.91 6.09 12 8.18V4z"/>
          </svg>
        </button>
      </div>

      <!-- Scrollable Snap-Paged Container -->
      <div class="scrollable-snap-wrapper" ref="scrollContainer">
        
        <!-- ==========================================
             PAGE 1: MAIN INVITATION CARD (Photo 2)
             ========================================== -->
        <section class="snap-page section-invitation-cover" id="page-invite">
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

            <!-- Scroll Down Prompt Indicator -->
            <div class="scroll-down-cue" @click="scrollToPage('page-countdown')">
              <ChevronDown :size="22" class="bounce-down-icon" />
            </div>

          </div>
        </section>

        <!-- ==========================================
             PAGE 2: COUNTDOWN & COUPLE PHOTO (Photo 3)
             ========================================== -->
        <section class="snap-page section-countdown-page" id="page-countdown">
          <div class="countdown-page-inner">
            
            <!-- Vintage Ornate "Click to Save The Date" Button -->
            <div class="save-date-button-wrap">
              <button class="vintage-save-date-btn" @click="handleSaveDate">
                <div class="vintage-frame-corner top-left"></div>
                <div class="vintage-frame-corner top-right"></div>
                <div class="vintage-frame-corner bottom-left"></div>
                <div class="vintage-frame-corner bottom-right"></div>
                <span class="btn-khmer-lbl">ចុចកត់ត្រាថ្ងៃកម្មវិធី</span>
                <span class="btn-en-lbl">Click to Save The Date</span>
                <div class="btn-gold-shimmer"></div>
              </button>
            </div>

            <!-- Event Countdown Header Section -->
            <div class="countdown-header-block">
              <h2 class="countdown-main-kh">ចំនួនថ្ងៃរាប់ថយក្រោយ</h2>
              <div class="gold-filigree-divider">
                <span class="diamond-point">❖</span>
                <span class="gold-line"></span>
                <span class="center-ornament">❦</span>
                <span class="gold-line"></span>
                <span class="diamond-point">❖</span>
              </div>
              <h3 class="countdown-sub-en">EVENT COUNTDOWN</h3>

              <!-- 4 Live Countdown Cards -->
              <div class="countdown-counter-grid">
                <div class="countdown-card">
                  <span class="num-text">{{ countdown.days }}</span>
                  <span class="label-text">ថ្ងៃ (Days)</span>
                </div>
                <span class="counter-colon">:</span>
                <div class="countdown-card">
                  <span class="num-text">{{ countdown.hours }}</span>
                  <span class="label-text">ម៉ោង (Hours)</span>
                </div>
                <span class="counter-colon">:</span>
                <div class="countdown-card">
                  <span class="num-text">{{ countdown.minutes }}</span>
                  <span class="label-text">នាទី (Mins)</span>
                </div>
                <span class="counter-colon">:</span>
                <div class="countdown-card">
                  <span class="num-text">{{ countdown.seconds }}</span>
                  <span class="label-text">វិនាទី (Secs)</span>
                </div>
              </div>
            </div>

            <!-- Congratulations Title & Romantic Couple Photo -->
            <div class="couple-photo-showcase">
              <h2 class="congratulations-title">Congratulations</h2>
              <p class="congratulations-kh">សូមអបអរសាទរគូស្វាមីភរិយាថ្មី</p>
              
              <div class="photo-frame-royal">
                <div class="photo-glow"></div>
                <img
                  :src="couplePhotoUrl"
                  alt="Khmer Wedding Couple in Traditional Gold Attire"
                  class="couple-main-img"
                />
                <div class="photo-inner-border"></div>
              </div>
            </div>

            <!-- Scroll Down Prompt to Timeline -->
            <div class="scroll-down-cue" @click="scrollToPage('page-timeline')">
              <ChevronDown :size="22" class="bounce-down-icon" />
            </div>

          </div>
        </section>

        <!-- ==========================================
             PAGE 3: WEDDING SCHEDULE TIMELINE (Photo 4 - Exact Match)
             ========================================== -->
        <section class="snap-page section-timeline-page" id="page-timeline">
          <div class="timeline-page-inner">
            
            <!-- Timeline Header (Exact Match to Reference Photo) -->
            <div class="schedule-page-header">
              <h3 class="schedule-date-kh">កម្មវិធីថ្ងៃសុក្រ ទី២៧ ខែមីនា ឆ្នាំ២០២៦</h3>
              <p class="schedule-address-kh">នៅភោជនីយដ្ឋាន សេនជូរីប្រាយ ផ្ទះលេខ ១០២ ផ្លូវលេខ ៣១៥</p>
              <p class="schedule-address-kh-sub">សង្កាត់បឹងកក់២ ខណ្ឌទួលគោក រាជធានីភ្នំពេញ</p>
              
            
            </div>

            <!-- Vertical Timeline Flow Directly on Sky Background (Matching Photo 4) -->
            <div class="schedule-timeline-flow">
              <div class="timeline-vertical-axis"></div>

              <!-- 1. 06:30 AM : Guest gathering (People at Banquet Table) -->
              <div class="schedule-step-item">
                <div class="step-icon-slot">
                  <svg viewBox="0 0 36 36" width="30" height="30" fill="none">
                    <!-- Center person -->
                    <circle cx="18" cy="10" r="3.2" stroke="#15325b" stroke-width="1.6" fill="#f0f7ff"/>
                    <path d="M12.5 21.5c0-3 2.5-5.5 5.5-5.5s5.5 2.5 5.5 5.5" stroke="#15325b" stroke-width="1.6" stroke-linecap="round"/>
                    <!-- Left person -->
                    <circle cx="9" cy="12" r="2.6" stroke="#15325b" stroke-width="1.5" fill="#f0f7ff"/>
                    <path d="M4.5 21.5c0-2.5 2-4.5 4.5-4.5s4.5 2 4.5 4.5" stroke="#15325b" stroke-width="1.5" stroke-linecap="round"/>
                    <!-- Right person -->
                    <circle cx="27" cy="12" r="2.6" stroke="#15325b" stroke-width="1.5" fill="#f0f7ff"/>
                    <path d="M22.5 21.5c0-2.5 2-4.5 4.5-4.5s4.5 2 4.5 4.5" stroke="#15325b" stroke-width="1.5" stroke-linecap="round"/>
                    <!-- Table line -->
                    <path d="M3 22h30" stroke="#15325b" stroke-width="1.8" stroke-linecap="round"/>
                  </svg>
                </div>
                <div class="step-content-slot">
                  <div class="step-khmer-title">
                    <span class="step-time">០៦:៣០ ព្រឹក</span>
                    <span class="step-sep">:</span>
                    <span class="step-name">ជួបជុំភ្ញៀវកិត្តិយសទាំងអស់</span>
                  </div>
                </div>
              </div>

              <!-- 2. 06:45 AM : Fruit carrying (Ceremonial Fruit Platter) -->
              <div class="schedule-step-item">
                <div class="step-icon-slot">
                  <svg viewBox="0 0 36 36" width="30" height="30" fill="none">
                    <!-- Ceremonial Fruit Cones / Baskets -->
                    <path d="M8 17c0-4 3-7 6-7s6 3 6 7" stroke="#15325b" stroke-width="1.5" fill="#f0f7ff"/>
                    <path d="M16 17c0-4 3-7 6-7s6 3 6 7" stroke="#15325b" stroke-width="1.5" fill="#f0f7ff"/>
                    <path d="M12 14c0-4 3-6.5 6-6.5s6 2.5 6 6.5" stroke="#15325b" stroke-width="1.5" fill="#f0f7ff"/>
                    <!-- Platter Tray Base -->
                    <path d="M4 17h28c0 3-3 6-7 6H11c-4 0-7-3-7-6z" stroke="#15325b" stroke-width="1.7" fill="#f0f7ff"/>
                    <path d="M14 23v4h8v-4" stroke="#15325b" stroke-width="1.6"/>
                    <path d="M11 27h14" stroke="#15325b" stroke-width="1.8" stroke-linecap="round"/>
                  </svg>
                </div>
                <div class="step-content-slot">
                  <div class="step-khmer-title">
                    <span class="step-time">០៦:៤៥ ព្រឹក</span>
                    <span class="step-sep">:</span>
                    <span class="step-name">ពិធីហែជំនូន(ផ្លែឈើ)</span>
                  </div>
                </div>
              </div>

              <!-- 3. 07:15 AM : Groom's Procession (Royal Pedestal Vase / Phan) -->
              <div class="schedule-step-item">
                <div class="step-icon-slot">
                  <svg viewBox="0 0 36 36" width="30" height="30" fill="none">
                    <!-- Flame / Lotus Bud Top -->
                    <path d="M18 4c-1.5 2.5-1.5 4.5 0 6 1.5-1.5 1.5-3.5 0-6z" fill="#d4af37" stroke="#15325b" stroke-width="1.2"/>
                    <!-- Top Offering Dome -->
                    <path d="M11 15c0-4 3.1-7 7-7s7 3 7 7H11z" stroke="#15325b" stroke-width="1.6" fill="#f0f7ff"/>
                    <!-- Tiered Pedestal Bowl -->
                    <path d="M7 15h22l-3 6H10l-3-6z" stroke="#15325b" stroke-width="1.6" fill="#f0f7ff"/>
                    <!-- Stem & Base -->
                    <path d="M15 21v5h6v-5" stroke="#15325b" stroke-width="1.5"/>
                    <path d="M10 26h16l2 4H8l2-4z" stroke="#15325b" stroke-width="1.6" fill="#f0f7ff"/>
                  </svg>
                </div>
                <div class="step-content-slot">
                  <div class="step-khmer-title">
                    <span class="step-time">០៧:១៥ ព្រឹក</span>
                    <span class="step-sep">:</span>
                    <span class="step-name">កូនកំលោះចូលរោងជ័យ(សំពះ)</span>
                  </div>
                </div>
              </div>

              <!-- 4. 08:05 AM : Ring wearing (Open Jewelry Box & Diamond Ring) -->
              <div class="schedule-step-item">
                <div class="step-icon-slot">
                  <svg viewBox="0 0 36 36" width="30" height="30" fill="none">
                    <!-- Diamond Sparkle Ring -->
                    <circle cx="18" cy="11" r="5" stroke="#15325b" stroke-width="1.7"/>
                    <polygon points="18,4 20.5,7 18,9.5 15.5,7" fill="#d4af37" stroke="#15325b" stroke-width="1.2"/>
                    <!-- Open Box Base -->
                    <rect x="7" y="15" width="22" height="13" rx="3" stroke="#15325b" stroke-width="1.7" fill="#f0f7ff"/>
                    <path d="M7 19h22" stroke="#15325b" stroke-width="1.3"/>
                  </svg>
                </div>
                <div class="step-content-slot">
                  <div class="step-khmer-title">
                    <span class="step-time">០៨:០៥ ព្រឹក</span>
                    <span class="step-sep">:</span>
                    <span class="step-name">ពិធីបំពាក់ចិញ្ចៀន</span>
                  </div>
                </div>
              </div>

              <!-- 5. 08:30 AM : Monk blessing (Praying Seated Monk) -->
              <div class="schedule-step-item">
                <div class="step-icon-slot">
                  <svg viewBox="0 0 36 36" width="30" height="30" fill="none">
                    <!-- Monk Head & Halo -->
                    <circle cx="18" cy="9" r="3.2" stroke="#15325b" stroke-width="1.6" fill="#f0f7ff"/>
                    <path d="M12 9a6 6 0 0 1 12 0" stroke="#d4af37" stroke-width="1.2" stroke-dasharray="1 2"/>
                    <!-- Robe & Meditating Body -->
                    <path d="M12 18c0-3.5 2.5-6 6-6s6 2.5 6 6l2 7H10l2-7z" stroke="#15325b" stroke-width="1.6" fill="#f0f7ff"/>
                    <!-- Praying Hands (Anjali) -->
                    <path d="M17 15l1-2 1 2v3h-2v-3z" stroke="#15325b" stroke-width="1.2" fill="#d4af37"/>
                    <!-- Lotus / Meditation Mat Base -->
                    <path d="M7 26c3-1 8-1 11-1s8 0 11 1c0 2-3 3-11 3S7 28 7 26z" stroke="#15325b" stroke-width="1.5" fill="#f0f7ff"/>
                  </svg>
                </div>
                <div class="step-content-slot">
                  <div class="step-khmer-title">
                    <span class="step-time">០៨:៣០ ព្រឹក</span>
                    <span class="step-sep">:</span>
                    <span class="step-name">ពិធីសូត្រមន្តចម្រើនព្រះបរិត្ត</span>
                  </div>
                </div>
              </div>

              <!-- 6. 09:30 AM : Hair cutting (Scissors & Comb Ceremony) -->
              <div class="schedule-step-item">
                <div class="step-icon-slot">
                  <svg viewBox="0 0 36 36" width="30" height="30" fill="none">
                    <!-- Scissors Handles -->
                    <circle cx="10" cy="11" r="3.5" stroke="#15325b" stroke-width="1.6"/>
                    <circle cx="10" cy="23" r="3.5" stroke="#15325b" stroke-width="1.6"/>
                    <!-- Crossed Scissors Blades -->
                    <line x1="13" y1="12" x2="26" y2="21" stroke="#15325b" stroke-width="1.7" stroke-linecap="round"/>
                    <line x1="13" y1="22" x2="26" y2="13" stroke="#15325b" stroke-width="1.7" stroke-linecap="round"/>
                    <circle cx="19.5" cy="17" r="1.2" fill="#d4af37"/>
                  </svg>
                </div>
                <div class="step-content-slot">
                  <div class="step-khmer-title">
                    <span class="step-time">០៩:៣០ ព្រឹក</span>
                    <span class="step-sep">:</span>
                    <span class="step-name">ពិធីកាត់សក់បង្កក់សិរី</span>
                  </div>
                </div>
              </div>

              <!-- 7. 10:15 AM : Tying the knot (Traditional Blessing Thread / Chong Dai) -->
              <div class="schedule-step-item">
                <div class="step-icon-slot">
                  <svg viewBox="0 0 36 36" width="30" height="30" fill="none">
                    <!-- Horizontal Sacred Cotton Cord -->
                    <path d="M4 17h8m12 0h8" stroke="#15325b" stroke-width="1.8" stroke-linecap="round"/>
                    <!-- Intricate Sacred Knot -->
                    <circle cx="18" cy="17" r="5" stroke="#15325b" stroke-width="1.6" fill="#f0f7ff"/>
                    <path d="M15 14c1.5-1.5 4.5-1.5 6 0s-1.5 4.5-3 6-3-4.5-3-6z" stroke="#d4af37" stroke-width="1.3" fill="#d4af37" fill-opacity="0.3"/>
                    <circle cx="18" cy="17" r="1.6" fill="#15325b"/>
                  </svg>
                </div>
                <div class="step-content-slot">
                  <div class="step-khmer-title">
                    <span class="step-time">១០:១៥ ព្រឹក</span>
                    <span class="step-sep">:</span>
                    <span class="step-name">ពិធីសែនចងដៃកូនចៅ</span>
                  </div>
                </div>
              </div>

              <!-- 8. 11:15 AM : Lunch banquet (Dining Plate, Cloche & Utensils) -->
              <div class="schedule-step-item">
                <div class="step-icon-slot">
                  <svg viewBox="0 0 36 36" width="30" height="30" fill="none">
                    <!-- Left Fork -->
                    <path d="M8 9v6a2 2 0 0 0 2 2v10" stroke="#15325b" stroke-width="1.5" stroke-linecap="round"/>
                    <path d="M6 9v4m4-4v4" stroke="#15325b" stroke-width="1.3" stroke-linecap="round"/>
                    <!-- Center Plate & Cloche -->
                    <circle cx="18" cy="18" r="8" stroke="#15325b" stroke-width="1.6" fill="#f0f7ff"/>
                    <circle cx="18" cy="18" r="5" stroke="#15325b" stroke-width="1.2"/>
                    <!-- Right Knife / Spoon -->
                    <path d="M28 9v18m-2-18c0 4 2 6 2 6" stroke="#15325b" stroke-width="1.5" stroke-linecap="round"/>
                  </svg>
                </div>
                <div class="step-content-slot">
                  <div class="step-khmer-title">
                    <span class="step-time">១១:១៥ ថ្ងៃត្រង់</span>
                    <span class="step-sep">:</span>
                    <span class="step-name">អញ្ជើញភ្ញៀវកិត្តិយសពិសាអាហារថ្ងៃត្រង់</span>
                  </div>
                </div>
              </div>

              <!-- 9. 05:00 PM : Dinner banquet (Clinking Champagne Glasses & Toast) -->
              <div class="schedule-step-item">
                <div class="step-icon-slot">
                  <svg viewBox="0 0 36 36" width="30" height="30" fill="none">
                    <!-- Left Glass (Tilted) -->
                    <path d="M12 6h6l-2 9a2.5 2.5 0 0 1-2.5 2.2h-.5A2.5 2.5 0 0 1 10.5 15L12 6z" stroke="#15325b" stroke-width="1.5" fill="#f0f7ff" transform="rotate(-15 13 12)"/>
                    <path d="M11 20l-1 8m-3 0h6" stroke="#15325b" stroke-width="1.5" stroke-linecap="round"/>
                    <!-- Right Glass (Tilted) -->
                    <path d="M20 6h6l-1.5 9a2.5 2.5 0 0 1-2.5 2.2h-.5a2.5 2.5 0 0 1-2.5-2.2L20 6z" stroke="#15325b" stroke-width="1.5" fill="#f0f7ff" transform="rotate(15 23 12)"/>
                    <path d="M25 20l1 8m-3 0h6" stroke="#15325b" stroke-width="1.5" stroke-linecap="round"/>
                    <!-- Clink Sparkle Stars -->
                    <circle cx="18" cy="8" r="1.4" fill="#d4af37"/>
                    <path d="M18 4v2m0 4v2m-3-5h2m4 0h2" stroke="#d4af37" stroke-width="1.2" stroke-linecap="round"/>
                  </svg>
                </div>
                <div class="step-content-slot">
                  <div class="step-khmer-title">
                    <span class="step-time">០៥:០០ ល្ងាច</span>
                    <span class="step-sep">:</span>
                    <span class="step-name">អញ្ជើញភ្ញៀវកិត្តិយសពិសាភោជនាហារពេលល្ងាច នៅភោជនីយដ្ឋាន សេនជូរីប្រាយ ដោយមេត្រីភាព</span>
                  </div>
                </div>
              </div>

            </div>

            <!-- Bottom Spacer to clear fixed nav -->
            <div class="timeline-bottom-spacer"></div>

          </div>
        </section>

        <!-- ==========================================
             PAGE 4: VENUE & WISHES
             ========================================== -->
        <section class="snap-page section-venue-wishes" id="page-venue">
          <div class="venue-wishes-inner">
            
            <!-- Venue Location Card -->
            <div class="venue-location-card">
              <h3 class="venue-card-title">ទីតាំងប្រារព្ធពិធី (Venue Location)</h3>
              <p class="venue-loc-name">ភោជនីយដ្ឋាន សេនជូរីប្រាយ</p>
              <p class="venue-loc-sub">Century Bright Restaurant, Phnom Penh</p>
              
              <a
                href="https://maps.google.com/?q=Century+Bright+Restaurant+Phnom+Penh"
                target="_blank"
                rel="noopener noreferrer"
                class="map-direct-btn"
                @click="playChimeSound"
              >
                <MapPin :size="18" /> បើកមើលផែនទី (Open in Google Maps)
              </a>
            </div>

            <!-- Guestbook Card -->
            <div class="guestbook-card">
              <h3 class="guestbook-title">សៀវភៅប្រសិទ្ធពរជ័យ (Guest Wishes)</h3>
              
              <form @submit.prevent="submitWish" class="wish-form">
                <input
                  type="text"
                  v-model="wishSender"
                  placeholder="ឈ្មោះរបស់អ្នក (Your Name)"
                  class="wish-input"
                  required
                />
                <textarea
                  v-model="wishMessage"
                  placeholder="សូមសរសេរពាក្យជូនពរនៅទីនេះ... (Your Blessing Message)"
                  class="wish-textarea"
                  rows="3"
                  required
                ></textarea>
                <button type="submit" class="wish-btn" @click="playChimeSound">
                  <MessageCircle :size="18" /> ផ្ញើពាក្យជូនពរ (Send Blessing)
                </button>
                <p v-if="wishSent" class="wish-sent-msg">✨ សូមអរគុណសម្រាប់ពាក្យជូនពរដ៏មានអត្ថន័យ!</p>
              </form>
            </div>

            <div class="timeline-bottom-spacer"></div>
          </div>
        </section>

      </div>

      <!-- Bottom Floating 4-Button Navigation Bar (Matching Photo) -->
      <div class="bottom-action-nav">
        <button
          class="nav-action-btn"
          :class="{ active: activeTab === 'invite' }"
          @click="scrollToPage('page-invite')"
          title="លិខិតអញ្ជើញ (Invitation Card)"
        >
          <CalendarDays :size="22" stroke-width="1.8" />
        </button>
        <button
          class="nav-action-btn"
          :class="{ active: activeTab === 'venue' }"
          @click="scrollToPage('page-venue')"
          title="ទីតាំង (Venue Location)"
        >
          <MapPin :size="22" stroke-width="1.8" />
        </button>
        <button
          class="nav-action-btn"
          :class="{ active: activeTab === 'timeline' }"
          @click="scrollToPage('page-timeline')"
          title="កម្មវិធី (Wedding Timeline Schedule)"
        >
          <Image :size="22" stroke-width="1.8" />
        </button>
        <button
          class="nav-action-btn"
          :class="{ active: activeTab === 'countdown' }"
          @click="scrollToPage('page-countdown')"
          title="រាប់ថយក្រោយ (Countdown & Photo)"
        >
          <MessageCircle :size="22" stroke-width="1.8" />
        </button>
      </div>

    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import ParticleEffects from './ParticleEffects.vue'
import rawMonogramUrl from '../assets/sapphire_m_crest_pure.jpg'
import invitationBgUrl from '../assets/background2.jpg'
import couplePhotoUrl from '../assets/couple_portrait.jpg'
import { CalendarDays, MapPin, Image, MessageCircle, ChevronDown } from 'lucide-vue-next'

const monogramUrl = ref(rawMonogramUrl)
const isPlaying = ref(false)
const scrollContainer = ref(null)
const activeTab = ref('invite')

const wishSender = ref('')
const wishMessage = ref('')
const wishSent = ref(false)

// Web Audio API Sound Synthesizer matching Sapphire Blue & Gold UI Theme
let audioCtx = null
let melodyTimer = null
let noteIndex = 0

// Romantic Royal Wedding Melodies in F Major / D Major chords
const weddingHarpNotes = [
  349.23, 440.00, 523.25, 698.46, // F4, A4, C5, F5
  261.63, 329.63, 392.00, 523.25, // C4, E4, G4, C5
  293.66, 349.23, 440.00, 587.33, // D4, F4, A4, D5
  233.08, 293.66, 349.23, 466.16, // Bb3, D4, F4, Bb4
  349.23, 440.00, 523.25, 698.46, 
  392.00, 493.88, 587.33, 783.99, // G4, B4, D5, G5
  523.25, 659.25, 783.99, 1046.50 // C5, E5, G5, C6
]

const bassNotes = [174.61, 130.81, 146.83, 116.54, 174.61, 196.00, 261.63]

function initAudioContext() {
  if (!audioCtx) {
    const AudioContextClass = window.AudioContext || window.webkitAudioContext
    if (AudioContextClass) {
      audioCtx = new AudioContextClass()
    }
  }
  if (audioCtx && audioCtx.state === 'suspended') {
    audioCtx.resume()
  }
}

// Gentle crystal chime note
function playHarpNote(freq, type = 'sine', duration = 1.4, gainValue = 0.08) {
  if (!audioCtx || audioCtx.state !== 'running') return
  try {
    const osc = audioCtx.createOscillator()
    const gain = audioCtx.createGain()
    const filter = audioCtx.createBiquadFilter()

    osc.type = type
    osc.frequency.setValueAtTime(freq, audioCtx.currentTime)

    // Warm resonant lowpass filter for gentle royal harp timbre
    filter.type = 'lowpass'
    filter.frequency.setValueAtTime(1600, audioCtx.currentTime)

    gain.gain.setValueAtTime(0.001, audioCtx.currentTime)
    gain.gain.exponentialRampToValueAtTime(gainValue, audioCtx.currentTime + 0.06)
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

// UI Click Chime Sound Effect
function playChimeSound() {
  initAudioContext()
  if (!audioCtx) return
  playHarpNote(880, 'sine', 0.6, 0.07)
  setTimeout(() => playHarpNote(1318.51, 'triangle', 0.8, 0.05), 80)
}

function startMelodyLoop() {
  if (melodyTimer) clearInterval(melodyTimer)
  
  melodyTimer = setInterval(() => {
    if (!isPlaying.value) return
    const freq = weddingHarpNotes[noteIndex % weddingHarpNotes.length]
    
    // Primary harp bell
    playHarpNote(freq, 'sine', 1.8, 0.085)
    
    // Golden overtone shimmer
    if (noteIndex % 2 === 0) {
      playHarpNote(freq * 1.5, 'triangle', 1.2, 0.035)
    }

    // Warm deep bass note every 4 beats
    if (noteIndex % 4 === 0) {
      const bassFreq = bassNotes[(noteIndex / 4) % bassNotes.length]
      playHarpNote(bassFreq, 'sine', 2.4, 0.06)
    }

    noteIndex++
  }, 500)
}

function toggleMusic() {
  initAudioContext()
  isPlaying.value = !isPlaying.value

  if (isPlaying.value) {
    playChimeSound()
    startMelodyLoop()
  } else {
    if (melodyTimer) clearInterval(melodyTimer)
  }
}

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

// Live Countdown Timer to 27 March 2026
const targetDate = new Date('2026-03-27T17:00:00')
const countdown = ref({ days: '00', hours: '00', minutes: '00', seconds: '00' })
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

function handleSaveDate() {
  playChimeSound()
  const calendarUrl = 'https://calendar.google.com/calendar/render?action=TEMPLATE&text=Wedding+Ceremony+%7C+%E1%9E%9F%E1%9E%B7%E1%9E%9A%E1%9E%B8%E1%9E%98%E1%9E%84%E1%9F%8D%E1%9E%82%E1%9E%9D%E1%9E%96%E1%9E%B6%E1%9E%9E%E1%9E%B7%E1%9E%96%E1%9E%B6%E1%9E%9E&dates=20260327T100000Z/20260327T150000Z&details=Wedding+Invitation+Celebration&location=Century+Bright+Restaurant+Phnom+Penh'
  window.open(calendarUrl, '_blank')
}

function scrollToPage(pageId) {
  playChimeSound()
  if (pageId === 'page-invite') activeTab.value = 'invite'
  if (pageId === 'page-countdown') activeTab.value = 'countdown'
  if (pageId === 'page-timeline') activeTab.value = 'timeline'
  if (pageId === 'page-venue') activeTab.value = 'venue'

  const el = document.getElementById(pageId)
  if (el) {
    el.scrollIntoView({ behavior: 'smooth', block: 'start' })
  }
}

function submitWish() {
  if (wishSender.value.trim() && wishMessage.value.trim()) {
    wishSent.value = true
    setTimeout(() => {
      wishSender.value = ''
      wishMessage.value = ''
    }, 3000)
  }
}

onMounted(() => {
  processTransparentImage(rawMonogramUrl)
  updateCountdown()
  timer = setInterval(updateCountdown, 1000)
})

onUnmounted(() => {
  if (timer) clearInterval(timer)
  if (melodyTimer) clearInterval(melodyTimer)
  if (audioCtx) audioCtx.close()
})
</script>

<style lang="scss" scoped>
$sapphire-dark: #1e3a5f;
$sapphire-navy: #15325b;
$sapphire-blue: #2563eb;
$gold-primary: #d4af37;
$gold-light: #fef08a;
$khmer-title-font: 'Moul', 'Bayon', 'Koulen', serif;
$khmer-body-font: 'Kantumruy Pro', 'Battambang', sans-serif;

.save-the-date-page {
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
  object-position: center top;
  display: block;
}

.bg-gradient-overlay {
  position: absolute;
  inset: 0;
  background: radial-gradient(
    ellipse at 50% 50%,
    rgba(255, 255, 255, 0.3) 0%,
    rgba(240, 248, 255, 0.1) 60%,
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
  position: relative;
  width: 40px;
  height: 40px;
  border-radius: 12px;
  background: rgba(255, 255, 255, 0.82);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  border: 1px solid rgba(255, 255, 255, 0.95);
  color: $sapphire-navy;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 14px rgba(15, 23, 42, 0.15);
  cursor: pointer;
  transition: all 0.25s ease;

  &:hover {
    transform: scale(1.06);
    background: rgba(255, 255, 255, 0.98);
  }

  &.active {
    background: linear-gradient(135deg, #1d4ed8 0%, #0e306e 100%);
    color: #ffffff;
    box-shadow: 0 4px 14px rgba(29, 78, 216, 0.4);
  }
}

.sound-waves-indicator {
  position: absolute;
  top: -4px;
  right: -4px;
  display: flex;
  gap: 1.5px;
  align-items: flex-end;
  height: 8px;

  .bar {
    width: 2px;
    background: #60a5fa;
    border-radius: 1px;
  }
  .bar-1 { height: 4px; animation: waveBounce 0.6s infinite alternate; }
  .bar-2 { height: 8px; animation: waveBounce 0.8s infinite alternate 0.2s; }
  .bar-3 { height: 5px; animation: waveBounce 0.7s infinite alternate 0.4s; }
}

@keyframes waveBounce {
  0% { height: 2px; }
  100% { height: 8px; }
}

/* Scrollable Snap Container */
.scrollable-snap-wrapper {
  position: relative;
  z-index: 10;
  width: 100%;
  height: 100%;
  overflow-y: auto;
  overflow-x: hidden;
  scroll-behavior: smooth;
  scroll-snap-type: y mandatory;
  scrollbar-width: none;
  -ms-overflow-style: none;

  &::-webkit-scrollbar {
    display: none;
  }
}

.snap-page {
  width: 100%;
  min-height: 100vh;
  min-height: 100dvh;
  scroll-snap-align: start;
  scroll-snap-stop: always;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  box-sizing: border-box;
}

/* ========================================================
   PAGE 1: INVITATION COVER (Photo 2)
   ======================================================== */
.section-invitation-cover {
  justify-content: flex-start;
}

.invitation-content {
  width: 100%;
  max-width: 440px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 16vh 16px 14px 16px;
  box-sizing: border-box;
  text-align: center;
  margin: 0 auto;

  @media (max-height: 750px) {
    padding-top: 13vh;
  }

  @media (max-height: 650px) {
    padding-top: 11vh;
  }
}

/* Monogram Section */
.monogram-section {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 0;
  margin-bottom: 2px;
  height: 68px;

  @media (max-height: 700px) {
    height: 56px;
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
  font-size: 1.4rem;
  font-weight: 400;
  color: $sapphire-navy;
  margin: 2px auto 6px auto;
  text-align: center;
  width: 100%;
  letter-spacing: 0.5px;
  line-height: 1.4;
  text-shadow: 0 1px 3px rgba(255, 255, 255, 0.95), 0 0 10px rgba(255, 255, 255, 0.8);
  filter: drop-shadow(0 1px 2px rgba(255, 255, 255, 0.9));

  @media (max-width: 380px) {
    font-size: 1.25rem;
  }

  @media (max-height: 700px) {
    font-size: 1.18rem;
    margin: 2px auto 4px auto;
  }
}

/* Parents Grid (2 Columns) */
.parents-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  width: 100%;
  max-width: 390px;
  gap: 10px;
  margin: 4px auto 6px auto;
  padding: 0 4px;
  justify-content: center;

  @media (max-height: 700px) {
    margin: 2px auto 4px auto;
    gap: 6px;
  }
}

.parent-col {
  display: flex;
  flex-direction: column;
  gap: 3px;

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
  font-size: 0.84rem;
  font-weight: 700;
  color: #1e3a5f;
  white-space: nowrap;

  @media (max-width: 380px) {
    font-size: 0.76rem;
  }
}

.name-text {
  font-size: 0.84rem;
  font-weight: 700;
  color: #1e3a5f;
  white-space: nowrap;

  @media (max-width: 380px) {
    font-size: 0.76rem;
  }
}

/* Honor Invitation Subtitle */
.honor-invite-title {
  font-family: $khmer-title-font;
  font-size: 0.94rem;
  font-weight: 400;
  color: #15325b;
  margin: 6px 0 4px 0;
  line-height: 1.4;
  text-shadow: 0 1px 3px rgba(255, 255, 255, 0.95);

  @media (max-height: 700px) {
    font-size: 0.86rem;
    margin: 3px 0 3px 0;
  }
}

/* Formal Invitation Text */
.formal-invitation-text {
  font-family: $khmer-body-font;
  font-size: 0.76rem;
  line-height: 1.45;
  color: #24416b;
  margin: 4px 0 8px 0;
  padding: 0 4px;
  font-weight: 500;
  text-shadow: 0 1px 2px rgba(255, 255, 255, 0.95);

  p {
    margin: 2px 0;
  }

  @media (max-width: 380px) {
    font-size: 0.7rem;
  }

  @media (max-height: 700px) {
    font-size: 0.68rem;
    line-height: 1.35;
    margin: 2px 0 4px 0;
  }
}

/* Couple Names Grid (2 Columns) */
.couple-names-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  width: 100%;
  gap: 14px;
  margin: 6px 0 8px 0;

  @media (max-height: 700px) {
    margin: 3px 0 4px 0;
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
  font-size: 0.8rem;
  font-weight: 600;
  color: #3b5c87;

  @media (max-width: 380px) {
    font-size: 0.74rem;
  }
}

.couple-name {
  font-family: $khmer-title-font;
  font-size: 1.15rem;
  font-weight: 400;
  color: #15325b;
  margin: 0;
  line-height: 1.3;

  @media (max-width: 380px) {
    font-size: 1.02rem;
  }

  @media (max-height: 700px) {
    font-size: 0.98rem;
  }
}

/* Date & Time Section */
.wedding-datetime-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
  margin: 6px 0 8px 0;
  font-family: $khmer-body-font;

  @media (max-height: 700px) {
    margin: 3px 0 4px 0;
    gap: 1px;
  }
}

.khmer-lunar-date {
  font-size: 0.76rem;
  font-weight: 500;
  color: #24416b;
  margin: 0;

  @media (max-width: 380px) {
    font-size: 0.7rem;
  }
}

.solar-date-highlight {
  font-size: 0.92rem;
  font-weight: 700;
  color: #102a4f;
  margin: 1px 0;

  @media (max-width: 380px) {
    font-size: 0.85rem;
  }
}

.reception-time {
  font-size: 0.82rem;
  font-weight: 600;
  color: #1e3a5f;
  margin: 0;

  @media (max-width: 380px) {
    font-size: 0.75rem;
  }
}

/* Venue Section */
.venue-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1px;
  margin: 4px 0 4px 0;
  font-family: $khmer-body-font;

  @media (max-height: 700px) {
    margin: 2px 0 2px 0;
  }
}

.venue-main-name {
  font-family: $khmer-title-font;
  font-size: 0.95rem;
  font-weight: 400;
  color: #15325b;
  margin: 0 0 1px 0;

  @media (max-width: 380px) {
    font-size: 0.88rem;
  }
}

.venue-address-line {
  font-size: 0.74rem;
  font-weight: 500;
  color: #24416b;
  margin: 0;

  @media (max-width: 380px) {
    font-size: 0.68rem;
  }
}

.venue-closing-wish {
  font-size: 0.76rem;
  font-weight: 600;
  color: #15325b;
  margin: 2px 0 0 0;
}

/* Scroll Down Cue */
.scroll-down-cue {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 6px;
  cursor: pointer;
  color: #15325b;
  transition: transform 0.2s ease;

  &:hover {
    transform: translateY(3px);
  }
}

.bounce-down-icon {
  animation: bounceDown 1.8s infinite ease-in-out;
}

@keyframes bounceDown {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(6px); }
}

/* ========================================================
   PAGE 2: COUNTDOWN & COUPLE SHOWCASE (Photo 3)
   ======================================================== */
.section-countdown-page {
  justify-content: flex-start;
}

.countdown-page-inner {
  width: 100%;
  max-width: 440px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 16vh 18px 20px 18px;
  box-sizing: border-box;
  text-align: center;
  margin: 0 auto;

  @media (max-height: 750px) {
    padding-top: 13vh;
  }
}

.save-date-button-wrap {
  width: 100%;
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.vintage-save-date-btn {
  position: relative;
  display: inline-flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 8px 30px;
  background: rgba(255, 255, 255, 0.9);
  border: 1.5px solid #8d6b38;
  border-radius: 18px;
  box-shadow: 0 4px 16px rgba(141, 107, 56, 0.2), inset 0 0 10px rgba(254, 240, 138, 0.4);
  cursor: pointer;
  overflow: hidden;
  transition: all 0.3s ease;

  &:hover {
    transform: scale(1.04);
    background: #ffffff;
    border-color: #b45309;
  }
}

.vintage-frame-corner {
  position: absolute;
  width: 8px;
  height: 8px;
  border-color: #8d6b38;
  border-style: solid;

  &.top-left { top: 3px; left: 3px; border-width: 1.5px 0 0 1.5px; }
  &.top-right { top: 3px; right: 3px; border-width: 1.5px 1.5px 0 0; }
  &.bottom-left { bottom: 3px; left: 3px; border-width: 0 0 1.5px 1.5px; }
  &.bottom-right { bottom: 3px; right: 3px; border-width: 0 1.5px 1.5px 0; }
}

.btn-khmer-lbl {
  font-family: $khmer-title-font;
  font-size: 1.05rem;
  color: #451a03;
  line-height: 1.3;
}

.btn-en-lbl {
  font-family: 'Cinzel', serif;
  font-size: 0.68rem;
  font-weight: 700;
  color: #78350f;
  letter-spacing: 1.5px;
}

.btn-gold-shimmer {
  position: absolute;
  top: 0;
  left: -100%;
  width: 60%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(254, 240, 138, 0.6), transparent);
  transform: skewX(-25deg);
  animation: buttonShimmer 4s infinite;
}

@keyframes buttonShimmer {
  0%, 70% { left: -100%; }
  100% { left: 200%; }
}

/* Event Countdown Block */
.countdown-header-block {
  width: 100%;
  max-width: 420px;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 22px;
  text-align: center;
}

.countdown-main-kh {
  font-family: $khmer-title-font;
  font-size: 1.25rem;
  color: #15325b;
  margin: 0 0 3px 0;
  text-shadow: 0 1px 3px rgba(255, 255, 255, 0.95);
}

.gold-filigree-divider {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  margin: 3px 0 5px 0;
  color: #b45309;

  .gold-line {
    width: 36px;
    height: 1.5px;
    background: linear-gradient(90deg, transparent, #d4af37, transparent);
  }

  .diamond-point { font-size: 0.7rem; color: #d4af37; }
  .center-ornament { font-size: 0.9rem; color: #1d4ed8; }
}

.countdown-sub-en {
  font-family: 'Cinzel', serif;
  font-size: 0.92rem;
  font-weight: 700;
  letter-spacing: 3.5px;
  color: #15325b;
  margin: 0 0 14px 0;
}

.countdown-counter-grid {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  width: 100%;
}

.countdown-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-width: 58px;
  padding: 6px 4px;
  background: rgba(255, 255, 255, 0.9);
  border: 1.5px solid rgba(212, 175, 55, 0.6);
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(15, 23, 42, 0.1);

  .num-text {
    font-family: 'Cinzel', monospace;
    font-size: 1.3rem;
    font-weight: 700;
    color: #15325b;
    line-height: 1.1;
  }

  .label-text {
    font-family: $khmer-body-font;
    font-size: 0.65rem;
    font-weight: 600;
    color: #78350f;
    margin-top: 2px;
  }
}

.counter-colon {
  font-family: 'Cinzel', monospace;
  font-size: 1.25rem;
  font-weight: 700;
  color: #b45309;
}

/* Couple Photo Showcase */
.couple-photo-showcase {
  width: 100%;
  max-width: 420px;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 16px;
  text-align: center;
}

.congratulations-title {
  font-family: 'Playfair Display', serif;
  font-size: 1.5rem;
  font-weight: 700;
  color: #15325b;
  margin: 0;
  letter-spacing: 1px;
}

.congratulations-kh {
  font-family: $khmer-title-font;
  font-size: 0.92rem;
  color: #78350f;
  margin: 3px 0 12px 0;
}

.photo-frame-royal {
  position: relative;
  width: 100%;
  border-radius: 18px;
  overflow: hidden;
  box-shadow: 0 12px 30px rgba(15, 23, 42, 0.3);
  border: 2px solid rgba(212, 175, 55, 0.7);

  .photo-glow {
    position: absolute;
    inset: 0;
    box-shadow: inset 0 0 20px rgba(0, 0, 0, 0.25);
    pointer-events: none;
    z-index: 2;
  }

  .couple-main-img {
    width: 100%;
    height: auto;
    display: block;
    object-fit: cover;
  }
}

/* ========================================================
   PAGE 3: WEDDING SCHEDULE TIMELINE (Photo 4 - Exact Match)
   ======================================================== */
.section-timeline-page {
  justify-content: flex-start;
}

.timeline-page-inner {
  width: 100%;
  max-width: 410px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 23vh 20px 24px 20px;
  box-sizing: border-box;
  margin: 0 auto;

  @media (max-height: 750px) {
    padding-top: 19vh;
  }

  @media (max-height: 650px) {
    padding-top: 17vh;
  }
}

.schedule-page-header {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  margin-bottom: 14px;

  .schedule-date-kh {
    font-family: $khmer-title-font;
    font-size: 1.15rem;
    color: #15325b;
    margin: 0 0 4px 0;
    line-height: 1.35;
    text-shadow: 0 1px 3px rgba(255, 255, 255, 0.95);
  }

  .schedule-address-kh {
    font-family: $khmer-body-font;
    font-size: 0.86rem;
    font-weight: 700;
    color: #1e3a5f;
    margin: 0;
    line-height: 1.35;
    text-shadow: 0 1px 2px rgba(255, 255, 255, 0.95);
  }

  .schedule-address-kh-sub {
    font-family: $khmer-body-font;
    font-size: 0.84rem;
    font-weight: 600;
    color: #24416b;
    margin: 2px 0 2px 0;
    text-shadow: 0 1px 2px rgba(255, 255, 255, 0.95);
  }
}

.schedule-timeline-flow {
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 11px;
  width: 100%;
  padding-left: 8px;
  box-sizing: border-box;
}

.timeline-vertical-axis {
  position: absolute;
  top: 10px;
  bottom: 14px;
  left: 40px;
  width: 1.5px;
  background: rgba(21, 50, 91, 0.3);
  z-index: 1;
}

.schedule-step-item {
  position: relative;
  display: flex;
  align-items: center;
  gap: 14px;
  z-index: 2;
}

.step-icon-slot {
  flex-shrink: 0;
  width: 32px;
  height: 32px;
  display: flex;
  justify-content: center;
  align-items: center;

  svg {
    filter: drop-shadow(0 1px 1px rgba(255, 255, 255, 0.9));
  }
}

.step-content-slot {
  display: flex;
  flex-direction: column;
  gap: 1px;
  text-align: left;
  padding-left: 4px;
}

.step-khmer-title {
  display: flex;
  flex-wrap: wrap;
  align-items: baseline;
  gap: 4px;
  font-family: $khmer-body-font;
  line-height: 1.35;
  text-shadow: 0 1px 2px rgba(255, 255, 255, 0.95);

  .step-time {
    font-size: 0.86rem;
    font-weight: 700;
    color: #15325b;
    white-space: nowrap;
  }

  .step-sep {
    font-weight: 700;
    color: #15325b;
  }

  .step-name {
    font-size: 0.86rem;
    font-weight: 700;
    color: #15325b;
  }
}

.timeline-bottom-spacer {
  height: 80px;
  width: 100%;
}

/* ========================================================
   PAGE 4: VENUE & WISHES
   ======================================================== */
.section-venue-wishes {
  justify-content: flex-start;
}

.venue-wishes-inner {
  width: 100%;
  max-width: 440px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 13vh 16px 20px 16px;
  box-sizing: border-box;
}

.venue-location-card {
  width: 100%;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  border-radius: 20px;
  border: 1px solid rgba(212, 175, 55, 0.5);
  padding: 20px 16px;
  margin-bottom: 20px;
  text-align: center;
  box-shadow: 0 6px 20px rgba(15, 23, 42, 0.08);
}

.venue-card-title {
  font-family: $khmer-title-font;
  font-size: 1.05rem;
  color: #15325b;
  margin: 0 0 4px 0;
}

.venue-loc-name {
  font-family: $khmer-title-font;
  font-size: 1rem;
  color: #1d4ed8;
  margin: 0 0 2px 0;
}

.venue-loc-sub {
  font-family: 'Cinzel', serif;
  font-size: 0.72rem;
  color: #64748b;
  margin: 0 0 12px 0;
}

.map-direct-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: 100%;
  padding: 12px 16px;
  border-radius: 14px;
  background: linear-gradient(135deg, #1d4ed8 0%, #1e3a8a 100%);
  color: #ffffff;
  font-family: $khmer-body-font;
  font-size: 0.92rem;
  font-weight: 700;
  text-decoration: none;
  box-shadow: 0 4px 14px rgba(29, 78, 216, 0.3);
  transition: all 0.25s ease;

  &:hover {
    transform: translateY(-2px);
  }
}

.guestbook-card {
  width: 100%;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  border-radius: 20px;
  border: 1px solid rgba(212, 175, 55, 0.5);
  padding: 20px 16px;
  margin-bottom: 20px;
  box-shadow: 0 6px 20px rgba(15, 23, 42, 0.08);
}

.guestbook-title {
  font-family: $khmer-title-font;
  font-size: 1.05rem;
  color: #15325b;
  text-align: center;
  margin: 0 0 12px 0;
}

.wish-form {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.wish-input, .wish-textarea {
  width: 100%;
  padding: 10px 14px;
  border-radius: 12px;
  border: 1px solid #cbd5e1;
  font-family: $khmer-body-font;
  font-size: 0.88rem;
  background: #ffffff;
  box-sizing: border-box;

  &:focus {
    outline: none;
    border-color: #2563eb;
    box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.15);
  }
}

.wish-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: 100%;
  padding: 12px;
  border-radius: 14px;
  background: linear-gradient(135deg, #b45309 0%, #78350f 100%);
  color: #ffffff;
  font-family: $khmer-body-font;
  font-size: 0.92rem;
  font-weight: 700;
  border: none;
  cursor: pointer;
  box-shadow: 0 4px 14px rgba(180, 83, 9, 0.3);
  transition: all 0.25s ease;

  &:hover {
    transform: translateY(-2px);
  }
}

.wish-sent-msg {
  font-family: $khmer-body-font;
  font-size: 0.88rem;
  font-weight: 700;
  color: #059669;
  text-align: center;
  margin: 4px 0 0 0;
}

/* ========================================================
   BOTTOM NAVIGATION BAR (4 Glass Cards)
   ======================================================== */
.bottom-action-nav {
  position: absolute;
  bottom: 16px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 8px 14px;
  background: rgba(255, 255, 255, 0.76);
  backdrop-filter: blur(14px);
  -webkit-backdrop-filter: blur(14px);
  border: 1px solid rgba(255, 255, 255, 0.95);
  border-radius: 20px;
  box-shadow: 0 8px 24px rgba(15, 35, 70, 0.15);
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

  &.active {
    background: #ffffff;
    color: #1d4ed8;
    border-color: #93c5fd;
    box-shadow: 0 4px 12px rgba(29, 78, 216, 0.25);
  }

  &:active {
    transform: scale(0.95);
  }
}
</style>
