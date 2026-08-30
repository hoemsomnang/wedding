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
            
            <!-- Main Wedding Ceremony Title -->
            <h1 class="main-wedding-title">សិរីមង្គលអាពាហ៍ពិពាហ៍</h1>

            <!-- Parents Section (2 Columns) -->
            <div class="parents-grid">
              <div class="parent-col left-col">
                <div class="parent-row">
                  <span class="role-text">លោក</span>
                  <span class="name-text">ហ៊ឹម លាង</span>
                </div>
                <div class="parent-row">
                  <span class="role-text">លោកស្រី</span>
                  <span class="name-text">អ៊ុំ ស្រ៊ឺ</span>
                </div>
              </div>

              <div class="parent-col right-col">
                <div class="parent-row">
                  <span class="role-text">លោក</span>
                  <span class="name-text">ខន សារេត</span>
                </div>
                <div class="parent-row">
                  <span class="role-text">លោកស្រី</span>
                  <span class="name-text">ធៀ ម៉ុំ</span>
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
                <h2 class="couple-name">ហ៊ឹម សំណាង</h2>
              </div>
              <div class="couple-col bride-col">
                <span class="couple-role">កូនស្រីនាម</span>
                <h2 class="couple-name">ខន សារ៉េន</h2>
              </div>
            </div>

            <!-- Wedding Auspicious Date & Time -->
            <div class="wedding-datetime-section">
              <p class="khmer-lunar-date">នៅថ្ងៃសៅរ៍ ៦កើត ខែផល្គុន ឆ្នាំមមី អដ្ឋស័ក ពុទ្ធសករាជ ២៥៧០</p>
              <p class="solar-date-highlight">ត្រូវនឹងថ្ងៃទី ១៣ ខែមីនា ឆ្នាំ ២០២៧</p>
              <p class="reception-time">វេលាម៉ោង ០៥ : ០០ ល្ងាចនៅ</p>
            </div>

            <!-- Wedding Reception Venue -->
            <div class="venue-section">
              <h3 class="venue-main-name">គេហដ្ឋាននៃសិរីមង្គលអាពាហ៍ពិពាហ៍</h3>
              <p class="venue-address-line">ស្ថិតនៅ ស្រុកសំពៅលូន ខេត្តបាត់ដំបង</p>
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
              <button class="vintage-save-date-btn" @click="addToCalendar" aria-label="Save the date to calendar">
                <!-- Ornate Vector Cartouche Frame -->
                <svg class="cartouche-frame-svg" viewBox="0 0 280 66" fill="none" preserveAspectRatio="none">
                  <defs>
                    <linearGradient id="plaqueGrad" x1="0%" y1="0%" x2="0%" y2="100%">
                      <stop offset="0%" stop-color="#ffffff" stop-opacity="0.96" />
                      <stop offset="45%" stop-color="#fdfbf6" stop-opacity="0.94" />
                      <stop offset="100%" stop-color="#f5ecd8" stop-opacity="0.96" />
                    </linearGradient>
                    <filter id="plaqueShadow" x="-10%" y="-10%" width="120%" height="130%">
                      <feDropShadow dx="0" dy="3" stdDeviation="3" flood-color="#4a361c" flood-opacity="0.18" />
                    </filter>
                  </defs>
                  
                  <!-- Outer Plaque Shape with Scallop / Bracket Corners -->
                  <path
                    d="M 28,5 
                       L 252,5 
                       C 261,5 267,11 267,19 
                       C 267,23 270.5,26 274.5,26 
                       C 276.5,26 277.5,27.5 277.5,33 
                       C 277.5,38.5 276.5,40 274.5,40 
                       C 270.5,40 267,43 267,47 
                       C 267,55 261,61 252,61 
                       L 28,61 
                       C 19,61 13,55 13,47 
                       C 13,43 9.5,40 5.5,40 
                       C 3.5,40 2.5,38.5 2.5,33 
                       C 2.5,27.5 3.5,26 5.5,26 
                       C 9.5,26 13,23 13,19 
                       C 13,11 19,5 28,5 Z"
                    fill="url(#plaqueGrad)"
                    stroke="#8c6c44"
                    stroke-width="1.6"
                    filter="url(#plaqueShadow)"
                  />

                  <!-- Inner Inset Filigree Border -->
                  <path
                    d="M 30,9 
                       L 250,9 
                       C 257,9 262,14 262,20 
                       C 262,24 265,26.5 269,27.5 
                       C 270.2,28.5 271,30 271,33 
                       C 271,36 270.2,37.5 269,38.5 
                       C 265,39.5 262,42 262,46 
                       C 262,52 257,57 250,57 
                       L 30,57 
                       C 23,57 18,52 18,46 
                       C 18,42 15,39.5 11,38.5 
                       C 9.8,37.5 9,36 9,33 
                       C 9,30 9.8,28.5 11,27.5 
                       C 15,26.5 18,24 18,20 
                       C 18,14 23,9 30,9 Z"
                    fill="none"
                    stroke="#bda480"
                    stroke-width="0.9"
                  />

                  <!-- Left & Right Center Ear Accents -->
                  <circle cx="6.5" cy="33" r="1.8" fill="#8c6c44" />
                  <circle cx="273.5" cy="33" r="1.8" fill="#8c6c44" />

                  <!-- Corner Inset Accent Dots -->
                  <circle cx="22" cy="13" r="1.2" fill="#a48154" />
                  <circle cx="258" cy="13" r="1.2" fill="#a48154" />
                  <circle cx="22" cy="53" r="1.2" fill="#a48154" />
                  <circle cx="258" cy="53" r="1.2" fill="#a48154" />
                </svg>

                <!-- Plaque Text -->
                <span class="btn-khmer-lbl">ចុចកត់ត្រាថ្ងៃកម្មវិធី</span>
                <span class="btn-en-lbl">Click to Save The Date</span>
                <div class="btn-gold-shimmer"></div>
              </button>
            </div>

            <!-- Event Countdown Header Section -->
            <div class="countdown-header-block">
              <h2 class="countdown-main-kh">ចំនួនថ្ងៃរាប់ថយក្រោយ</h2>
              
              <!-- Exact Matching Filigree Divider -->
              <div class="filigree-divider-wrap">
                <svg class="filigree-divider-svg" viewBox="0 0 240 18" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <!-- Left horizontal line & terminal dot -->
                  <path d="M22 9 H82" stroke="#8d6b38" stroke-width="1.1" stroke-linecap="round" />
                  <circle cx="20" cy="9" r="1.5" fill="#8d6b38" />
                  <circle cx="85" cy="9" r="1.6" fill="#8d6b38" />
                  
                  <!-- Central intertwined oval knot motif -->
                  <ellipse cx="98" cy="9" rx="7.5" ry="4" stroke="#8d6b38" stroke-width="1.2" fill="none" />
                  <polygon points="120,4.5 124.5,9 120,13.5 115.5,9" fill="#8d6b38" />
                  <ellipse cx="142" cy="9" rx="7.5" ry="4" stroke="#8d6b38" stroke-width="1.2" fill="none" />
                  
                  <!-- Right horizontal line & terminal dot -->
                  <circle cx="155" cy="9" r="1.6" fill="#8d6b38" />
                  <path d="M158 9 H218" stroke="#8d6b38" stroke-width="1.1" stroke-linecap="round" />
                  <circle cx="220" cy="9" r="1.5" fill="#8d6b38" />
                </svg>
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
              <h3 class="schedule-date-kh">កម្មវិធីថ្ងៃសៅរ៍ ទី១៣ ខែមីនា ឆ្នាំ២០២៧</h3>
              <p class="schedule-address-kh">ប្រារព្ធនៅ ស្រុកសំពៅលូន ខេត្តបាត់ដំបង</p>
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
                    <span class="step-name">អញ្ជើញភ្ញៀវកិត្តិយសពិសាភោជនាហារពេលល្ងាច ដោយមេត្រីភាព</span>
                  </div>
                </div>
              </div>

            </div>

            <!-- Bottom Spacer to clear fixed nav -->
            <div class="timeline-bottom-spacer"></div>

          </div>
        </section>

        <!-- ==========================================
             PAGE 4: LOCATION & ROADMAP (Exact Match to Photo)
             ========================================== -->
        <section class="snap-page section-location-map-page" id="page-venue">
          <div class="location-map-inner">
            
            <!-- Centered Royal Location Header with Gold Filigree Wings -->
            <div class="location-page-header">
              <div class="location-title-badge">
                <div class="filigree-wing left">
                  <span class="sparkle-diamond">❖</span>
                  <span class="flourish-line"></span>
                </div>
                <h2 class="location-title-kh">ទីតាំងកម្មវិធី</h2>
                <div class="filigree-wing right">
                  <span class="flourish-line"></span>
                  <span class="sparkle-diamond">❖</span>
                </div>
              </div>
            </div>

            <!-- Illustrated Schematic Roadmap Art (Loaded as SVG Image Asset) -->
            <div class="roadmap-canvas-card" @click="openGoogleMaps" title="ចុចដើម្បីបើកផែនទី Google Maps">
              <img
                :src="roadmapMapSvgUrl"
                alt="Wedding Location Roadmap"
                class="roadmap-img"
              />
            </div>

            <!-- QR Code Section Linking Directly to Google Maps Location (Matching Photo) -->
            <div class="map-qrcode-card" @click="openGoogleMaps">
              <div class="qrcode-wrapper">
                <img
                  v-if="qrCodeDataUrl"
                  :src="qrCodeDataUrl"
                  alt="Google Maps QR Code"
                  class="qrcode-img"
                />
                <div v-else class="qrcode-skeleton"></div>
              </div>
              <!-- Vintage Cartouche Plaque Button (Matching Image) -->
              <button class="vintage-location-btn" @click.stop="openGoogleMaps" aria-label="Open location map in Google Maps">
                <!-- Ornate Vector Cartouche Frame -->
                <svg class="cartouche-frame-svg" viewBox="0 0 280 66" fill="none" preserveAspectRatio="none">
                  <defs>
                    <linearGradient id="locPlaqueGrad" x1="0%" y1="0%" x2="0%" y2="100%">
                      <stop offset="0%" stop-color="#ffffff" stop-opacity="0.96" />
                      <stop offset="45%" stop-color="#fdfbf6" stop-opacity="0.94" />
                      <stop offset="100%" stop-color="#f5ecd8" stop-opacity="0.96" />
                    </linearGradient>
                    <filter id="locPlaqueShadow" x="-10%" y="-10%" width="120%" height="130%">
                      <feDropShadow dx="0" dy="3" stdDeviation="3" flood-color="#4a361c" flood-opacity="0.18" />
                    </filter>
                  </defs>
                  
                  <!-- Outer Plaque Shape with Scallop / Bracket Corners -->
                  <path
                    d="M 28,5 
                       L 252,5 
                       C 261,5 267,11 267,19 
                       C 267,23 270.5,26 274.5,26 
                       C 276.5,26 277.5,27.5 277.5,33 
                       C 277.5,38.5 276.5,40 274.5,40 
                       C 270.5,40 267,43 267,47 
                       C 267,55 261,61 252,61 
                       L 28,61 
                       C 19,61 13,55 13,47 
                       C 13,43 9.5,40 5.5,40 
                       C 3.5,40 2.5,38.5 2.5,33 
                       C 2.5,27.5 3.5,26 5.5,26 
                       C 9.5,26 13,23 13,19 
                       C 13,11 19,5 28,5 Z"
                    fill="url(#locPlaqueGrad)"
                    stroke="#8c6c44"
                    stroke-width="1.6"
                    filter="url(#locPlaqueShadow)"
                  />

                  <!-- Inner Inset Filigree Border -->
                  <path
                    d="M 30,9 
                       L 250,9 
                       C 257,9 262,14 262,20 
                       C 262,24 265,26.5 269,27.5 
                       C 270.2,28.5 271,30 271,33 
                       C 271,36 270.2,37.5 269,38.5 
                       C 265,39.5 262,42 262,46 
                       C 262,52 257,57 250,57 
                       L 30,57 
                       C 23,57 18,52 18,46 
                       C 18,42 15,39.5 11,38.5 
                       C 9.8,37.5 9,36 9,33 
                       C 9,30 9.8,28.5 11,27.5 
                       C 15,26.5 18,24 18,20 
                       C 18,14 23,9 30,9 Z"
                    fill="none"
                    stroke="#bda480"
                    stroke-width="0.9"
                  />

                  <!-- Left & Right Center Ear Accents -->
                  <circle cx="6.5" cy="33" r="1.8" fill="#8c6c44" />
                  <circle cx="273.5" cy="33" r="1.8" fill="#8c6c44" />

                  <!-- Corner Inset Accent Dots -->
                  <circle cx="22" cy="13" r="1.2" fill="#a48154" />
                  <circle cx="258" cy="13" r="1.2" fill="#a48154" />
                  <circle cx="22" cy="53" r="1.2" fill="#a48154" />
                  <circle cx="258" cy="53" r="1.2" fill="#a48154" />
                </svg>

                <!-- Plaque Text -->
                <span class="btn-khmer-lbl">ចុចមើលទីតាំង</span>
                <span class="btn-en-lbl">Click to View Location</span>
                <div class="btn-gold-shimmer"></div>
              </button>
            </div>

            <!-- Spacer before fixed bottom navigation bar -->
            <div class="location-bottom-spacer"></div>

          </div>
        </section>

        <!-- ==========================================
             PAGE 5: PHOTO GALLERY (Exact Match to Reference UI)
             ========================================== -->
        <section class="snap-page section-gallery-page" id="page-gallery">
          <div class="gallery-page-inner">
            
            <!-- Gallery Header with Left Leader Line -->
            <div class="gallery-page-header">
              <span class="header-left-line"></span>
              <h2 class="gallery-title-kh-en">
                <span class="kh-part">វិចិត្រសាល</span>
                <span class="slash-sep">/</span>
                <span class="en-part">PHOTO GALLERY</span>
              </h2>
            </div>

            <!-- Gallery Collage Grid with Scroll Fade-In & Fade-Out -->
            <div class="gallery-grid-flow">
              
              <!-- 1. Top Hero Landscape Photo Card -->
              <div class="gallery-card hero-card scroll-fade-item" @click="openLightbox(galleryHeroImg, 'ពិធីសិរីមង្គលអាពាហ៍ពិពាហ៍')">
                <div class="photo-card-frame">
                  <img :src="galleryHeroImg" alt="Wedding Hero Couple" class="gallery-photo-img" />
                  <div class="photo-card-sheen"></div>
                  <div class="photo-card-badge">
                    <Sparkles :size="12" class="sparkle-icon" /> រូបភាពពិសេស
                  </div>
                </div>
              </div>

              <!-- 2. Row 2: 2-Column Medium Photos -->
              <div class="gallery-row-2col scroll-fade-item">
                <div class="gallery-card sub-card" @click="openLightbox(galleryStandingImg, 'អនុស្សាវរីយ៍គូស្នេហ៍')">
                  <div class="photo-card-frame">
                    <img :src="galleryStandingImg" alt="Wedding Standing Couple" class="gallery-photo-img fit-cover" />
                    <div class="photo-card-sheen"></div>
                  </div>
                </div>
                <div class="gallery-card sub-card" @click="openLightbox(couplePhotoUrl, 'ស្នាមញញឹមនៃក្តីស្រលាញ់')">
                  <div class="photo-card-frame">
                    <img :src="couplePhotoUrl" alt="Wedding Couple Portrait" class="gallery-photo-img fit-cover" />
                    <div class="photo-card-sheen"></div>
                  </div>
                </div>
              </div>

              <!-- 3. Row 3: 3-Column Portrait Photos -->
              <div class="gallery-row-3col scroll-fade-item">
                <div class="gallery-card portrait-card" @click="openLightbox(galleryStandingImg, 'សិរីមង្គលអាពាហ៍ពិពាហ៍')">
                  <div class="photo-card-frame">
                    <img :src="galleryStandingImg" alt="Wedding Portrait Standing" class="gallery-photo-img fit-cover" />
                    <div class="photo-card-sheen"></div>
                  </div>
                </div>
                <div class="gallery-card portrait-card" @click="openLightbox(galleryHeroImg, 'សុភមង្គលគូស្នេហ៍')">
                  <div class="photo-card-frame">
                    <img :src="galleryHeroImg" alt="Wedding Portrait Anjali" class="gallery-photo-img fit-cover" />
                    <div class="photo-card-sheen"></div>
                  </div>
                </div>
                <div class="gallery-card portrait-card" @click="openLightbox(galleryArchImg, 'ស្បថសច្ចានៃក្តីស្រលាញ់')">
                  <div class="photo-card-frame">
                    <img :src="galleryArchImg" alt="Wedding Portrait Arch" class="gallery-photo-img fit-cover" />
                    <div class="photo-card-sheen"></div>
                  </div>
                </div>
              </div>

              <!-- 4. Row 4: 2-Column Arched Window Frames -->
              <div class="gallery-row-arch-2col scroll-fade-item">
                <div class="gallery-card arch-card" @click="openLightbox(galleryArchImg, 'ស្នេហ៍និរន្តរ៍')">
                  <div class="photo-arch-frame">
                    <img :src="galleryArchImg" alt="Wedding Romantic Arch" class="gallery-photo-img fit-cover" />
                    <div class="photo-card-sheen"></div>
                  </div>
                </div>
                <div class="gallery-card arch-card" @click="openLightbox(galleryArchImg, 'ពេលវេលាដ៏មានន័យ')">
                  <div class="photo-arch-frame monochrome-tone">
                    <img :src="galleryArchImg" alt="Wedding Romantic Arch Monotone" class="gallery-photo-img fit-cover" />
                    <div class="photo-card-sheen"></div>
                  </div>
                </div>
              </div>

              <!-- 5. Row 5 (NEW): Fine Art Rings & Garden Stroll -->
              <div class="gallery-row-2col scroll-fade-item">
                <div class="gallery-card sub-card" @click="openLightbox(galleryRingsImg, 'ចិញ្ចៀនមង្គលការ & ផ្កាឈូកស')">
                  <div class="photo-card-frame">
                    <img :src="galleryRingsImg" alt="Wedding Rings and Lotus" class="gallery-photo-img fit-cover" />
                    <div class="photo-card-sheen"></div>
                  </div>
                </div>
                <div class="gallery-card sub-card" @click="openLightbox(galleryGardenImg, 'ដំណើរជីវិតរួមគ្នា')">
                  <div class="photo-card-frame">
                    <img :src="galleryGardenImg" alt="Royal Garden Wedding Stroll" class="gallery-photo-img fit-cover" />
                    <div class="photo-card-sheen"></div>
                  </div>
                </div>
              </div>

              <!-- 6. Row 6 (NEW): Horizontal Memory Reel Strip -->
              <div class="gallery-reel-section scroll-fade-item">
                <div class="reel-header-badge">
                  <span class="reel-label-kh">ផ្ទាំងរូបភាពអនុស្សាវរីយ៍បន្ថែម</span>
                </div>
                <div class="gallery-horizontal-reel">
                  <div class="reel-card" @click="openLightbox(galleryGardenImg, 'សួនស្នេហ៍សុភមង្គល')">
                    <img :src="galleryGardenImg" alt="Memory 1" class="reel-img" />
                  </div>
                  <div class="reel-card" @click="openLightbox(galleryHeroImg, 'ពិធីមង្គលការ')">
                    <img :src="galleryHeroImg" alt="Memory 2" class="reel-img" />
                  </div>
                  <div class="reel-card" @click="openLightbox(galleryStandingImg, 'សម្លៀកបំពាក់ប្រពៃណីខ្មែរ')">
                    <img :src="galleryStandingImg" alt="Memory 3" class="reel-img" />
                  </div>
                  <div class="reel-card" @click="openLightbox(galleryRingsImg, 'ចិញ្ចៀនអាពាហ៍ពិពាហ៍')">
                    <img :src="galleryRingsImg" alt="Memory 4" class="reel-img" />
                  </div>
                  <div class="reel-card" @click="openLightbox(galleryArchImg, 'ស្បថសច្ចានៃក្តីស្រលាញ់')">
                    <img :src="galleryArchImg" alt="Memory 5" class="reel-img" />
                  </div>
                  <div class="reel-card" @click="openLightbox(couplePhotoUrl, 'អនុស្សាវរីយ៍គូស្នេហ៍')">
                    <img :src="couplePhotoUrl" alt="Memory 6" class="reel-img" />
                  </div>
                </div>
              </div>

            </div>

            <!-- Spacer before fixed bottom navigation bar -->
            <div class="gallery-bottom-spacer"></div>

          </div>
        </section>

        <!-- ==========================================
             PAGE 6: OUR GRATITUDE (សេចក្តីថ្លែងអំណរគុណ - Exact Match to Photo)
             ========================================== -->
        <section class="snap-page section-gratitude-page" id="page-gratitude">
          <div class="gratitude-page-inner">
            
            <div class="gratitude-card-glass">
              <!-- Top Royal Sparkle Emblem -->
              <div class="gratitude-top-emblem">
                <span class="emblem-sparkle">✦</span>
              </div>

              <!-- Main Khmer Title -->
              <h2 class="gratitude-title-kh">សេចក្តីថ្លែងអំណរគុណ</h2>

              <!-- Body Paragraph 1 -->
              <p class="gratitude-text-p1">
                យើងខ្ញុំជាមាតាបិតានៃ <strong>កូនប្រុស-កូនស្រី</strong><br />
                សូមគោរពថ្លែងអំណរគុណយ៉ាងជ្រាលជ្រៅបំផុតចំពោះ<br />
                ឯកឧត្តម លោកជំទាវ លោកអ្នកឧកញ៉ា អ្នកឧកញ៉ា ឧកញ៉ា លោក លោកស្រី អ្នកនាង កញ្ញា ដែលបានអញ្ជើញចូលរួមជាអធិបតី និងជាភ្ញៀវកិត្តិយសក្នុង ពិធីមង្គលអាពាហ៍ពិពាហ៍ កូនប្រុស-កូនស្រី យើងខ្ញុំ។
              </p>

              <!-- Body Paragraph 2 -->
              <p class="gratitude-text-p2">
                យើងខ្ញុំសូមគោរពសម្តែងនូវការរំភើបចិត្តខ្ពង់ខ្ពស់បំផុតជូន ឯកឧត្តម លោកជំទាវ លោកអ្នកឧកញ៉ា អ្នកឧកញ៉ា ឧកញ៉ា លោក លោកស្រី អ្នកនាង កញ្ញា និងភ្ញៀវកិត្តិយស សូមទទួលបាននូវពរទាំងបួនប្រការគឺ <strong>អាយុ វណ្ណៈ សុខៈ ពលៈ</strong> កុំបីឃ្លៀងឃ្លាតឡើយ។
              </p>

              <!-- Final Thank You Line -->
              <p class="gratitude-thanks-line">សូមអរគុណ !</p>

              <!-- Ornate Filigree Divider (Matching Reference Photo) -->
              <div class="gratitude-filigree-divider">
                <svg viewBox="0 0 200 16" class="gratitude-divider-svg" fill="none">
                  <line x1="10" y1="8" x2="78" y2="8" stroke="#15325b" stroke-width="1.2" stroke-linecap="round" />
                  <circle cx="85" cy="8" r="2.2" fill="#c29a4b" />
                  <!-- Center Diamond Knot -->
                  <path d="M 100 2 L 106 8 L 100 14 L 94 8 Z" fill="#15325b" stroke="#c29a4b" stroke-width="0.8" />
                  <circle cx="100" cy="8" r="1.5" fill="#fef08a" />
                  <circle cx="115" cy="8" r="2.2" fill="#c29a4b" />
                  <line x1="122" y1="8" x2="190" y2="8" stroke="#15325b" stroke-width="1.2" stroke-linecap="round" />
                </svg>
              </div>
            </div>

            <!-- Bottom Spacer before fixed nav -->
            <div class="gratitude-bottom-spacer"></div>

          </div>
        </section>

      </div>

      <!-- ========================================================
           INTERACTIVE LIGHTBOX MODAL PREVIEW
           ======================================================== -->
      <transition name="lightbox-zoom">
        <div v-if="activeLightboxImg" class="lightbox-backdrop" @click.self="closeLightbox">
          <div class="lightbox-content-box">
            <button class="lightbox-close-btn" @click="closeLightbox" aria-label="Close Lightbox">
              <X :size="24" />
            </button>
            <img :src="activeLightboxImg" :alt="activeLightboxTitle" class="lightbox-zoom-img" />
            <p v-if="activeLightboxTitle" class="lightbox-caption">{{ activeLightboxTitle }}</p>
          </div>
        </div>
      </transition>

      <!-- ========================================================
           GUEST WISHES SLIDE-UP MODAL (When 4th nav tab clicked)
           ======================================================== -->
      <transition name="modal-fade">
        <div v-if="showWishesModal" class="wishes-modal-backdrop" @click.self="toggleWishesModal">
          <div class="wishes-modal-card">
            <div class="modal-header-row">
              <h3 class="modal-title-kh">សៀវភៅប្រសិទ្ធពរជ័យ</h3>
              <button class="modal-close-btn" @click="toggleWishesModal" aria-label="Close">
                <X :size="20" />
              </button>
            </div>
            
            <form @submit.prevent="submitWish" class="wish-modal-form">
              <input
                type="text"
                v-model="wishSender"
                placeholder="ឈ្មោះរបស់អ្នក (Your Name)"
                class="wish-modal-input"
                required
              />
              <textarea
                v-model="wishMessage"
                placeholder="សូមសរសេរពាក្យជូនពរនៅទីនេះ... (Your Blessing Message)"
                class="wish-modal-textarea"
                rows="3"
                required
              ></textarea>
              <button type="submit" class="wish-modal-btn" @click="playChimeSound">
                <Send :size="16" /> ផ្ញើពាក្យជូនពរ (Send Blessing)
              </button>
              <p v-if="wishSent" class="wish-modal-sent-msg">✨ សូមអរគុណសម្រាប់ពាក្យជូនពរដ៏មានអត្ថន័យ!</p>
            </form>
          </div>
        </div>
      </transition>

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
          :class="{ active: activeTab === 'gallery' }"
          @click="scrollToPage('page-gallery')"
          title="វិចិត្រសាល (Photo Gallery)"
        >
          <Image :size="22" stroke-width="1.8" />
        </button>
        <button
          class="nav-action-btn"
          :class="{ active: showWishesModal }"
          @click="toggleWishesModal"
          title="ពាក្យជូនពរ (Guest Wishes)"
        >
          <MessageCircle :size="22" stroke-width="1.8" />
        </button>
      </div>

    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import QRCode from 'qrcode'
import ParticleEffects from './ParticleEffects.vue'
import rawMonogramUrl from '../assets/sapphire_m_crest_pure.jpg'
import invitationBgUrl from '../assets/background2.jpg'
import couplePhotoUrl from '../assets/couple_portrait.jpg'
import roadmapMapSvgUrl from '../assets/wedding_roadmap_map.svg'
import galleryHeroImg from '../assets/gallery_hero.jpg'
import galleryStandingImg from '../assets/gallery_standing.jpg'
import galleryArchImg from '../assets/gallery_arch.jpg'
import galleryRingsImg from '../assets/gallery_rings.jpg'
import galleryGardenImg from '../assets/gallery_garden.jpg'
import { CalendarDays, MapPin, Image, MessageCircle, ChevronDown, ExternalLink, X, Send, Sparkles } from 'lucide-vue-next'

const monogramUrl = ref(rawMonogramUrl)
const isPlaying = ref(false)
const scrollContainer = ref(null)
const activeTab = ref('invite')
const showWishesModal = ref(false)

// Lightbox modal state
const activeLightboxImg = ref(null)
const activeLightboxTitle = ref('')

function openLightbox(img, title) {
  playChimeSound()
  activeLightboxImg.value = img
  activeLightboxTitle.value = title
}

function closeLightbox() {
  playChimeSound()
  activeLightboxImg.value = null
}

const qrCodeDataUrl = ref('')
const googleMapUrl = "https://www.google.com/maps/place/13%C2%B029'22.0%22N+102%C2%B022'05.2%22E/@13.4851043,102.3649696,16z/data=!4m4!3m3!8m2!3d13.4894418!4d102.3681016!18m1!1e1?entry=ttu&g_ep=EgoyMDI2MDgyNi4wIKXMDSoASAFQAw%3D%3D"

function openGoogleMaps() {
  try {
    playChimeSound()
  } catch (e) {}
  const targetWin = window.open(googleMapUrl, '_blank', 'noopener,noreferrer')
  if (!targetWin || targetWin.closed || typeof targetWin.closed === 'undefined') {
    window.location.href = googleMapUrl
  }
}

function toggleWishesModal() {
  try {
    playChimeSound()
  } catch (e) {}
  showWishesModal.value = !showWishesModal.value
}

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
  try {
    if (!audioCtx) {
      const AudioContextClass = window.AudioContext || window.webkitAudioContext
      if (AudioContextClass) {
        audioCtx = new AudioContextClass()
      }
    }
    if (audioCtx && audioCtx.state === 'suspended') {
      audioCtx.resume().catch(() => {})
    }
  } catch (e) {
    // Fail silently on restricted mobile browsers
  }
}

// Gentle crystal chime note
function playHarpNote(freq, type = 'sine', duration = 1.4, gainValue = 0.08) {
  try {
    if (!audioCtx || audioCtx.state !== 'running') return
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
    // Fail silently so it never interrupts clicks or scrolls
  }
}

// UI Click Chime Sound Effect
function playChimeSound() {
  try {
    initAudioContext()
    if (!audioCtx) return
    playHarpNote(880, 'sine', 0.6, 0.07)
    setTimeout(() => {
      try {
        playHarpNote(1318.51, 'triangle', 0.8, 0.05)
      } catch (e) {}
    }, 80)
  } catch (e) {}
}

function startMelodyLoop() {
  if (melodyTimer) clearInterval(melodyTimer)
  
  melodyTimer = setInterval(() => {
    try {
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
    } catch (e) {}
  }, 500)
}

function toggleMusic() {
  try {
    initAudioContext()
  } catch (e) {}
  isPlaying.value = !isPlaying.value

  if (isPlaying.value) {
    playChimeSound()
    startMelodyLoop()
  } else {
    if (melodyTimer) clearInterval(melodyTimer)
  }
}

// Live Countdown Timer to 13 March 2027
const targetDate = new Date('2027-03-13T17:00:00')
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
  try {
    playChimeSound()
  } catch (e) {}
  const calendarUrl = 'https://calendar.google.com/calendar/render?action=TEMPLATE&text=Wedding+Ceremony+%7C+%E1%9E%9F%E1%9E%B7%E1%9E%9A%E1%9E%B8%E1%9E%98%E1%9E%84%E1%9F%8D%E1%9E%82%E1%9E%9D%E1%9E%96%E1%9E%B6%E1%9E%9E%E1%9E%B7%E1%9E%96%E1%9E%B6%E1%9E%9E&dates=20270313T100000Z/20270313T150000Z&details=Wedding+Invitation+Celebration&location=Century+Bright+Restaurant+Phnom+Penh'
  const targetWin = window.open(calendarUrl, '_blank', 'noopener,noreferrer')
  if (!targetWin || targetWin.closed || typeof targetWin.closed === 'undefined') {
    window.location.href = calendarUrl
  }
}

function scrollToPage(pageId) {
  try {
    playChimeSound()
  } catch (e) {}
  if (pageId === 'page-invite') activeTab.value = 'invite'
  if (pageId === 'page-countdown') activeTab.value = 'countdown'
  if (pageId === 'page-timeline') activeTab.value = 'timeline'
  if (pageId === 'page-venue') activeTab.value = 'venue'
  if (pageId === 'page-gallery') activeTab.value = 'gallery'
  if (pageId === 'page-gratitude') activeTab.value = 'gallery'

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

const addToCalendar = handleSaveDate
let scrollObserver = null

onMounted(async () => {
  updateCountdown()
  timer = setInterval(updateCountdown, 1000)

  // Generate crisp vector-like QR code for Google Maps Location
  try {
    qrCodeDataUrl.value = await QRCode.toDataURL(googleMapUrl, {
      margin: 1,
      width: 220,
      color: {
        dark: '#15325b',
        light: '#ffffff'
      },
      errorCorrectionLevel: 'M'
    })
  } catch (err) {
    console.error('Error generating map QR code:', err)
  }

  // Smooth Scroll & Active Nav Spy
  const sectionMap = [
    { id: 'page-invite', tab: 'invite' },
    { id: 'page-countdown', tab: 'countdown' },
    { id: 'page-timeline', tab: 'timeline' },
    { id: 'page-venue', tab: 'venue' },
    { id: 'page-gallery', tab: 'gallery' },
    { id: 'page-gratitude', tab: 'gallery' }
  ]

  scrollObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const found = sectionMap.find(s => s.id === entry.target.id)
        if (found && !showWishesModal.value) {
          activeTab.value = found.tab
        }
      }
    })
  }, { threshold: 0.45 })

  sectionMap.forEach(s => {
    const el = document.getElementById(s.id)
    if (el) scrollObserver.observe(el)
  })

  // Scroll-Driven Fade-In & Fade-Out Observer for Photos
  const photoFadeObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('is-visible')
        entry.target.classList.remove('is-hidden')
      } else {
        entry.target.classList.remove('is-visible')
        entry.target.classList.add('is-hidden')
      }
    })
  }, { threshold: 0.1, rootMargin: '0px 0px -20px 0px' })

  document.querySelectorAll('.scroll-fade-item').forEach(el => {
    photoFadeObserver.observe(el)
  })
})

onUnmounted(() => {
  if (timer) clearInterval(timer)
  if (melodyTimer) clearInterval(melodyTimer)
  if (audioCtx) audioCtx.close()
  if (scrollObserver) scrollObserver.disconnect()
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
  mix-blend-mode: multiply;
  filter: drop-shadow(0 4px 8px rgba(21, 50, 91, 0.25));
  animation: gentleFloat 4s ease-in-out infinite alternate;
  will-change: transform;
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
  margin-bottom: 22px;
}

.vintage-save-date-btn {
  position: relative;
  display: inline-flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 246px;
  height: 54px;
  padding: 4px 18px;
  background: transparent;
  border: none;
  outline: none;
  cursor: pointer;
  overflow: visible;
  transition: transform 0.28s cubic-bezier(0.34, 1.56, 0.64, 1), filter 0.28s ease;
  filter: drop-shadow(0 3px 10px rgba(92, 69, 36, 0.16));

  &:hover {
    transform: scale(1.04);
    filter: drop-shadow(0 6px 16px rgba(92, 69, 36, 0.25));
  }

  &:active {
    transform: scale(0.98);
  }
}

.cartouche-frame-svg {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 1;
  overflow: visible;
}

.btn-khmer-lbl {
  position: relative;
  z-index: 2;
  font-family: $khmer-title-font;
  font-size: 0.98rem;
  font-weight: 400;
  color: #15325b;
  line-height: 1.25;
  margin-top: -1px;
  text-shadow: 0 1px 2px rgba(255, 255, 255, 0.8);
}

.btn-en-lbl {
  position: relative;
  z-index: 2;
  font-family: 'Playfair Display', Georgia, serif;
  font-style: italic;
  font-size: 0.68rem;
  font-weight: 600;
  color: #73532a;
  letter-spacing: 0.5px;
  margin-top: 1px;
  text-shadow: 0 1px 2px rgba(255, 255, 255, 0.8);
}

.btn-gold-shimmer {
  position: absolute;
  inset: 4px;
  border-radius: 12px;
  pointer-events: none;
  overflow: hidden;
  z-index: 3;

  &::after {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 50%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.45), transparent);
    transform: skewX(-25deg);
    animation: buttonShimmer 4.5s infinite;
  }
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
  margin-bottom: 20px;
  text-align: center;
}

.countdown-main-kh {
  font-family: $khmer-title-font;
  font-size: 1.22rem;
  font-weight: 400;
  color: #15325b;
  margin: 0 0 2px 0;
  text-shadow: 0 1px 3px rgba(255, 255, 255, 0.95);
}

.filigree-divider-wrap {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  max-width: 220px;
  margin: 2px auto 4px auto;
}

.filigree-divider-svg {
  width: 100%;
  height: auto;
  display: block;
}

.countdown-sub-en {
  font-family: 'Cinzel', serif;
  font-size: 0.92rem;
  font-weight: 700;
  letter-spacing: 4px;
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
  box-shadow: 0 12px 30px rgba(15, 23, 42, 0.3), 0 0 20px rgba(212, 175, 55, 0.25);
  border: 2px solid rgba(212, 175, 55, 0.7);
  transition: transform 0.4s ease, box-shadow 0.4s ease;
  animation: frameAuraPulse 6s infinite ease-in-out;

  &:hover {
    transform: scale(1.02);
    box-shadow: 0 16px 40px rgba(15, 23, 42, 0.35), 0 0 30px rgba(212, 175, 55, 0.5);
  }

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
    transition: transform 0.6s ease;
    animation: gentleBreathingPortrait 10s infinite ease-in-out alternate;
  }
}

@keyframes frameAuraPulse {
  0%, 100% { box-shadow: 0 12px 30px rgba(15, 23, 42, 0.3), 0 0 16px rgba(212, 175, 55, 0.2); }
  50% { box-shadow: 0 14px 34px rgba(15, 23, 42, 0.32), 0 0 28px rgba(212, 175, 55, 0.45); }
}

@keyframes gentleBreathingPortrait {
  0% { transform: scale(1); }
  100% { transform: scale(1.035); }
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
   PAGE 4: ILLUSTRATED LOCATION ROADMAP (Exact Match to Photo)
   ======================================================== */
.section-location-map-page {
  justify-content: flex-start;
}

.location-map-inner {
  width: 100%;
  max-width: 440px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 15vh 14px 16px 14px;
  box-sizing: border-box;
  margin: 0 auto;

  @media (max-height: 750px) {
    padding-top: 12vh;
  }

  @media (max-height: 650px) {
    padding-top: 10vh;
  }
}

.location-page-header {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  max-width: 380px;
  margin: 0 auto 10px auto;
  text-align: center;
}

.location-title-badge {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  padding: 4px 18px;
  border-radius: 20px;
  background: rgba(255, 255, 255, 0.45);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  border: 1px solid rgba(255, 255, 255, 0.85);
  box-shadow: 0 4px 16px rgba(21, 50, 91, 0.08);
}

.filigree-wing {
  display: flex;
  align-items: center;
  gap: 5px;

  .sparkle-diamond {
    font-size: 0.75rem;
    color: #c29a4b;
    line-height: 1;
    filter: drop-shadow(0 0 3px rgba(254, 240, 138, 0.8));
    animation: gentlePulse 3s infinite ease-in-out;
  }

  .flourish-line {
    width: 26px;
    height: 1.5px;
    background: linear-gradient(90deg, #c29a4b, #15325b);
    border-radius: 1px;
  }

  &.right .flourish-line {
    background: linear-gradient(90deg, #15325b, #c29a4b);
  }
}

.location-title-kh {
  font-family: $khmer-title-font;
  font-size: 1.25rem;
  font-weight: 400;
  color: #15325b;
  margin: 0;
  line-height: 1.3;
  letter-spacing: 0.5px;
  text-shadow: 0 1px 3px rgba(255, 255, 255, 0.95), 0 0 10px rgba(255, 255, 255, 0.85);
  white-space: nowrap;

  @media (max-width: 380px) {
    font-size: 1.12rem;
  }
}

@keyframes gentlePulse {
  0%, 100% { transform: scale(1); opacity: 0.9; }
  50% { transform: scale(1.15); opacity: 1; filter: drop-shadow(0 0 6px rgba(212, 175, 55, 0.9)); }
}

.roadmap-canvas-card {
  width: 100%;
  max-width: 360px;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  border-radius: 18px;
  padding: 4px;
  box-sizing: border-box;
  transition: transform 0.25s ease, filter 0.25s ease;

  &:hover {
    transform: scale(1.015);
    filter: drop-shadow(0 6px 20px rgba(21, 50, 91, 0.15));
  }
}

.roadmap-img {
  width: 100%;
  height: auto;
  max-height: 48vh;
  object-fit: contain;
  display: block;
  filter: drop-shadow(0 2px 8px rgba(21, 50, 91, 0.08));
}

/* QR Code Section */
.map-qrcode-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  margin-top: 2px;
  cursor: pointer;
  transition: transform 0.25s ease;

  &:hover {
    transform: scale(1.05);
  }
}

.qrcode-wrapper {
  padding: 4px;
  background: #ffffff;
  border: 1px solid rgba(21, 50, 91, 0.2);
  border-radius: 10px;
  box-shadow: 0 4px 14px rgba(21, 50, 91, 0.12);
  display: flex;
  align-items: center;
  justify-content: center;
}

.qrcode-img {
  width: 78px;
  height: 78px;
  display: block;
  border-radius: 6px;

  @media (max-height: 700px) {
    width: 66px;
    height: 66px;
  }
}

.qrcode-skeleton {
  width: 78px;
  height: 78px;
  background: rgba(21, 50, 91, 0.06);
  border-radius: 6px;
}

.vintage-location-btn {
  position: relative;
  display: inline-flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 220px;
  height: 50px;
  padding: 3px 16px;
  background: transparent;
  border: none;
  outline: none;
  cursor: pointer;
  overflow: visible;
  margin-top: 5px;
  transition: transform 0.28s cubic-bezier(0.34, 1.56, 0.64, 1), filter 0.28s ease;
  filter: drop-shadow(0 3px 10px rgba(92, 69, 36, 0.16));

  &:hover {
    transform: scale(1.04);
    filter: drop-shadow(0 6px 16px rgba(92, 69, 36, 0.25));
  }

  &:active {
    transform: scale(0.98);
  }

  .btn-khmer-lbl {
    position: relative;
    z-index: 2;
    font-family: $khmer-title-font;
    font-size: 0.94rem;
    font-weight: 400;
    color: #15325b;
    line-height: 1.25;
    margin-top: -1px;
    text-shadow: 0 1px 2px rgba(255, 255, 255, 0.8);
  }

  .btn-en-lbl {
    position: relative;
    z-index: 2;
    font-family: 'Playfair Display', Georgia, serif;
    font-style: italic;
    font-size: 0.66rem;
    font-weight: 600;
    color: #73532a;
    letter-spacing: 0.5px;
    margin-top: 1px;
    text-shadow: 0 1px 2px rgba(255, 255, 255, 0.8);
  }
}

.location-bottom-spacer {
  height: 70px;
  width: 100%;
}

/* ========================================================
   GUESTBOOK WISHES MODAL
   ======================================================== */
.wishes-modal-backdrop {
  position: fixed;
  inset: 0;
  background: rgba(11, 19, 43, 0.6);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 16px;
}

.wishes-modal-card {
  width: 100%;
  max-width: 380px;
  background: rgba(255, 255, 255, 0.95);
  border-radius: 20px;
  border: 1px solid rgba(212, 175, 55, 0.6);
  box-shadow: 0 12px 36px rgba(11, 19, 43, 0.35);
  padding: 20px;
  box-sizing: border-box;
}

.modal-header-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 14px;
  border-bottom: 1px solid rgba(21, 50, 91, 0.1);
  padding-bottom: 8px;
}

.modal-title-kh {
  font-family: $khmer-title-font;
  font-size: 1.05rem;
  color: #15325b;
  margin: 0;
}

.modal-close-btn {
  background: transparent;
  border: none;
  color: #64748b;
  cursor: pointer;
  padding: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
  transition: all 0.2s ease;

  &:hover {
    color: #15325b;
    background: rgba(21, 50, 91, 0.08);
  }
}

.wish-modal-form {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.wish-modal-input, .wish-modal-textarea {
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

.wish-modal-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: 100%;
  padding: 11px;
  border-radius: 12px;
  background: linear-gradient(135deg, #1d4ed8 0%, #15325b 100%);
  color: #ffffff;
  font-family: $khmer-body-font;
  font-size: 0.92rem;
  font-weight: 700;
  border: none;
  cursor: pointer;
  box-shadow: 0 4px 14px rgba(29, 78, 216, 0.3);
  transition: all 0.25s ease;

  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 18px rgba(29, 78, 216, 0.4);
  }
}

.wish-modal-sent-msg {
  font-family: $khmer-body-font;
  font-size: 0.88rem;
  font-weight: 700;
  color: #059669;
  text-align: center;
  margin: 4px 0 0 0;
}

/* Modal Transition */
.modal-fade-enter-active, .modal-fade-leave-active {
  transition: opacity 0.3s ease, transform 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}

.modal-fade-enter-from, .modal-fade-leave-to {
  opacity: 0;
  transform: scale(0.94);
}

/* ========================================================
   PAGE 5: PHOTO GALLERY (Exact Match to Reference UI)
   ======================================================== */
.section-gallery-page {
  justify-content: flex-start;
}

.gallery-page-inner {
  width: 100%;
  max-width: 440px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 14vh 14px 20px 14px;
  box-sizing: border-box;
  margin: 0 auto;

  @media (max-height: 750px) {
    padding-top: 11vh;
  }

  @media (max-height: 650px) {
    padding-top: 9vh;
  }
}

.gallery-page-header {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  gap: 10px;
  width: 100%;
  max-width: 366px;
  margin: 0 auto 8px auto;
  padding-left: 4px;
  box-sizing: border-box;
}

.gallery-title-kh-en {
  display: flex;
  align-items: baseline;
  gap: 6px;
  margin: 0;
  color: #15325b;
  text-shadow: 0 1px 4px rgba(255, 255, 255, 0.98), 0 0 14px rgba(255, 255, 255, 0.9);
  filter: drop-shadow(0 1px 2px rgba(255, 255, 255, 0.95));

  .kh-part {
    font-family: $khmer-title-font;
    font-size: 1.15rem;
    font-weight: 400;
    line-height: 1.25;
    letter-spacing: 0.5px;
    color: #15325b;
  }

  .slash-sep {
    font-family: 'Cinzel', serif;
    font-size: 1rem;
    font-weight: 700;
    color: #15325b;
    margin: 0 2px;
  }

  .en-part {
    font-family: 'Cinzel', serif;
    font-size: 1rem;
    font-weight: 700;
    letter-spacing: 1.8px;
    color: #15325b;
  }
}

.gallery-grid-flow {
  display: flex;
  flex-direction: column;
  gap: 8px;
  width: 100%;
  max-width: 366px;
}

.gallery-card {
  position: relative;
  cursor: pointer;
  transition: transform 0.35s cubic-bezier(0.16, 1, 0.3, 1), filter 0.35s ease;
  animation: photoCardEntrance 0.75s cubic-bezier(0.16, 1, 0.3, 1) both;

  &.hero-card { animation-delay: 0.08s; }
  &.delay-1 { animation-delay: 0.16s; }
  &.delay-2 { animation-delay: 0.24s; }
  &.delay-3 { animation-delay: 0.32s; }
  &.delay-4 { animation-delay: 0.38s; }
  &.delay-5 { animation-delay: 0.44s; }
  &.delay-6 { animation-delay: 0.50s; }
  &.delay-7 { animation-delay: 0.56s; }

  &:hover {
    transform: translateY(-4px) scale(1.025);
    z-index: 5;
  }

  &:active {
    transform: scale(0.97);
  }
}

@keyframes photoCardEntrance {
  0% {
    opacity: 0;
    transform: translateY(22px) scale(0.95);
  }
  100% {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

.photo-card-frame, .photo-arch-frame {
  position: relative;
  width: 100%;
  overflow: hidden;
  background: #ffffff;
  border: 2.2px solid rgba(255, 255, 255, 0.95);
  box-shadow: 0 4px 14px rgba(15, 35, 70, 0.12);
  box-sizing: border-box;
  transition: border-color 0.35s ease, box-shadow 0.35s ease;

  .gallery-card:hover & {
    border-color: #ffffff;
    box-shadow: 0 10px 26px rgba(21, 50, 91, 0.22), 0 0 16px rgba(212, 175, 55, 0.35);
  }
}

.photo-card-frame {
  border-radius: 12px;
}

.photo-arch-frame {
  border-radius: 60px 60px 10px 10px;

  &.monochrome-tone img {
    filter: contrast(1.05) brightness(0.98);
  }
}

.photo-card-sheen {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    115deg,
    transparent 25%,
    rgba(255, 255, 255, 0.35) 45%,
    rgba(255, 255, 255, 0.65) 50%,
    rgba(255, 255, 255, 0.35) 55%,
    transparent 75%
  );
  transform: translateX(-150%);
  pointer-events: none;
  z-index: 2;
  animation: photoSheenSweep 7s infinite ease-in-out;
}

.gallery-card.delay-1 .photo-card-sheen { animation-delay: 0.8s; }
.gallery-card.delay-2 .photo-card-sheen { animation-delay: 1.6s; }
.gallery-card.delay-3 .photo-card-sheen { animation-delay: 2.4s; }
.gallery-card.delay-4 .photo-card-sheen { animation-delay: 3.2s; }
.gallery-card.delay-5 .photo-card-sheen { animation-delay: 4.0s; }
.gallery-card.delay-6 .photo-card-sheen { animation-delay: 4.8s; }
.gallery-card.delay-7 .photo-card-sheen { animation-delay: 5.6s; }

@keyframes photoSheenSweep {
  0%, 70% { transform: translateX(-150%); }
  100% { transform: translateX(160%); }
}

.gallery-photo-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center top;
  display: block;
  transition: transform 0.5s cubic-bezier(0.16, 1, 0.3, 1), filter 0.4s ease;

  .gallery-card:hover & {
    transform: scale(1.07);
    filter: brightness(1.03);
  }
}

.gallery-card.hero-card .gallery-photo-img {
  animation: subtleLivingZoom 14s infinite ease-in-out alternate;
}

@keyframes subtleLivingZoom {
  0% { transform: scale(1); }
  100% { transform: scale(1.045); }
}

/* Row 1: Hero Card */
.gallery-card.hero-card .photo-card-frame {
  height: 185px;

  @media (max-height: 700px) {
    height: 165px;
  }
}

/* Row 2: 2-Columns */
.gallery-row-2col {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 8px;
  width: 100%;

  .photo-card-frame {
    height: 105px;

    @media (max-height: 700px) {
      height: 95px;
    }
  }
}

/* Row 3: 3-Columns Portrait */
.gallery-row-3col {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 6px;
  width: 100%;

  .photo-card-frame {
    height: 120px;

    @media (max-height: 700px) {
      height: 105px;
    }
  }
}

/* Row 4: 2-Columns Arch */
.gallery-row-arch-2col {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 8px;
  width: 100%;

  .photo-arch-frame {
    height: 125px;

    @media (max-height: 700px) {
      height: 110px;
    }
  }
}

/* Scroll Fade-In and Entrance Animation System (GPU-accelerated) */
.scroll-fade-item {
  opacity: 1;
  transform: translate3d(0, 0, 0);
  transition: opacity 0.5s cubic-bezier(0.16, 1, 0.3, 1),
              transform 0.5s cubic-bezier(0.16, 1, 0.3, 1);
  will-change: opacity, transform;
  content-visibility: auto;

  &.is-visible {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }

  &.is-hidden {
    opacity: 0.4;
    transform: translate3d(0, -8px, 0);
  }
}

/* Photo Card Badge */
.photo-card-badge {
  position: absolute;
  top: 8px;
  right: 8px;
  display: inline-flex;
  align-items: center;
  gap: 4px;
  padding: 3px 9px;
  border-radius: 12px;
  background: rgba(21, 50, 91, 0.75);
  backdrop-filter: blur(8px);
  border: 1px solid rgba(212, 175, 55, 0.6);
  color: #fef08a;
  font-family: $khmer-body-font;
  font-size: 0.68rem;
  font-weight: 600;
  z-index: 3;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);

  .sparkle-icon {
    color: #fde047;
    animation: gentlePulse 2s infinite ease-in-out;
  }
}

/* Memory Reel Section */
.gallery-reel-section {
  width: 100%;
  margin-top: 6px;
}

.reel-header-badge {
  text-align: center;
  margin-bottom: 6px;

  .reel-label-kh {
    font-family: $khmer-body-font;
    font-size: 0.76rem;
    font-weight: 700;
    color: #15325b;
    padding: 2px 10px;
    border-radius: 12px;
    background: rgba(255, 255, 255, 0.7);
    border: 1px solid rgba(21, 50, 91, 0.15);
    display: inline-block;
  }
}

.gallery-horizontal-reel {
  display: flex;
  gap: 10px;
  overflow-x: auto;
  padding: 4px 2px 8px 2px;
  scroll-snap-type: x mandatory;
  -webkit-overflow-scrolling: touch;
  scrollbar-width: none;
  &::-webkit-scrollbar { display: none; }
}

.reel-card {
  flex: 0 0 110px;
  height: 125px;
  border-radius: 12px;
  overflow: hidden;
  border: 2px solid #ffffff;
  box-shadow: 0 4px 12px rgba(15, 35, 70, 0.12);
  cursor: pointer;
  scroll-snap-align: center;
  transition: transform 0.3s ease, box-shadow 0.3s ease;

  &:hover {
    transform: translateY(-3px) scale(1.05);
    box-shadow: 0 8px 20px rgba(29, 78, 216, 0.25);
  }

  &:active {
    transform: scale(0.96);
  }
}

.reel-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* ========================================================
   PAGE 6: OUR GRATITUDE (សេចក្តីថ្លែងអំណរគុណ - Exact Match)
   ======================================================== */
.section-gratitude-page {
  justify-content: center;
}

.gratitude-page-inner {
  width: 100%;
  max-width: 440px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  min-height: 100dvh;
  padding: 16vh 20px 24px 20px;
  box-sizing: border-box;
  text-align: center;
  margin: 0 auto;

  @media (max-height: 750px) {
    padding-top: 13vh;
  }

  @media (max-height: 650px) {
    padding-top: 10vh;
  }
}

.gratitude-card-glass {
  width: 100%;
  max-width: 380px;
  background: rgba(255, 255, 255, 0.42);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border-radius: 24px;
  padding: 24px 20px 22px 20px;
  border: 1px solid rgba(255, 255, 255, 0.85);
  box-shadow: 0 10px 30px rgba(15, 35, 70, 0.08);
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  animation: photoCardEntrance 0.8s cubic-bezier(0.16, 1, 0.3, 1) both;
}

.gratitude-top-emblem {
  margin-bottom: 6px;

  .emblem-sparkle {
    font-size: 1rem;
    color: #c29a4b;
    filter: drop-shadow(0 0 4px rgba(254, 240, 138, 0.8));
    animation: gentlePulse 2.5s infinite ease-in-out;
  }
}

.gratitude-title-kh {
  font-family: $khmer-title-font;
  font-size: 1.35rem;
  font-weight: 400;
  color: #15325b;
  margin: 0 0 16px 0;
  line-height: 1.3;
  text-shadow: 0 1px 3px rgba(255, 255, 255, 0.95), 0 0 12px rgba(255, 255, 255, 0.8);

  @media (max-width: 380px) {
    font-size: 1.2rem;
  }
}

.gratitude-text-p1, .gratitude-text-p2 {
  font-family: $khmer-body-font;
  font-size: 0.86rem;
  font-weight: 500;
  color: #15325b;
  line-height: 1.8;
  margin: 0 0 14px 0;
  text-shadow: 0 1px 2px rgba(255, 255, 255, 0.9);

  strong {
    font-weight: 700;
    color: #0f2b52;
  }

  @media (max-width: 380px) {
    font-size: 0.8rem;
    line-height: 1.7;
  }
}

.gratitude-thanks-line {
  font-family: $khmer-title-font;
  font-size: 1.05rem;
  font-weight: 400;
  color: #15325b;
  margin: 8px 0 14px 0;
  text-shadow: 0 1px 3px rgba(255, 255, 255, 0.95);
}

.gratitude-filigree-divider {
  width: 100%;
  max-width: 220px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 4px auto 8px auto;
}

.gratitude-divider-svg {
  width: 100%;
  height: auto;
  display: block;
}

.gratitude-subtitle-en {
  font-family: 'Cinzel', serif;
  font-size: 1.05rem;
  font-weight: 700;
  letter-spacing: 3.5px;
  color: #15325b;
  margin: 4px 0 0 0;
  text-shadow: 0 1px 3px rgba(255, 255, 255, 0.9);

  @media (max-width: 380px) {
    font-size: 0.95rem;
    letter-spacing: 2.5px;
  }
}

.gratitude-bottom-spacer {
  height: 70px;
  width: 100%;
}

/* ========================================================
   LIGHTBOX MODAL
   ======================================================== */
.lightbox-backdrop {
  position: fixed;
  inset: 0;
  background: rgba(11, 19, 43, 0.88);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  z-index: 120;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 18px;
  cursor: zoom-out;
}

.lightbox-content-box {
  position: relative;
  max-width: 90vw;
  max-height: 85vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  cursor: default;
}

.lightbox-close-btn {
  position: absolute;
  top: -38px;
  right: 0;
  background: rgba(255, 255, 255, 0.25);
  border: 1px solid rgba(255, 255, 255, 0.4);
  color: #ffffff;
  border-radius: 50%;
  width: 34px;
  height: 34px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.2s ease;

  &:hover {
    background: rgba(255, 255, 255, 0.4);
    transform: scale(1.1);
  }
}

.lightbox-zoom-img {
  max-width: 100%;
  max-height: 76vh;
  object-fit: contain;
  border-radius: 14px;
  border: 3px solid #ffffff;
  box-shadow: 0 16px 48px rgba(0, 0, 0, 0.5);
}

.lightbox-caption {
  font-family: $khmer-title-font;
  font-size: 0.96rem;
  color: #ffffff;
  margin-top: 10px;
  text-align: center;
  text-shadow: 0 2px 8px rgba(0, 0, 0, 0.8);
}

.lightbox-zoom-enter-active, .lightbox-zoom-leave-active {
  transition: opacity 0.3s ease, transform 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}

.lightbox-zoom-enter-from, .lightbox-zoom-leave-to {
  opacity: 0;
  transform: scale(0.9);
}

/* ========================================================
   BOTTOM NAVIGATION BAR (4 Glass Cards Matching Photo)
   ======================================================== */
.bottom-action-nav {
  position: absolute;
  bottom: 16px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 7px 14px;
  background: rgba(255, 255, 255, 0.78);
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
  background: rgba(255, 255, 255, 0.88);
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
    box-shadow: 0 4px 14px rgba(29, 78, 216, 0.3);
  }

  &:active {
    transform: scale(0.95);
  }
}
</style>
