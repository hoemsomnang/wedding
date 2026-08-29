<template>
  <div class="app-layout">
    <!-- Main Transition Container (Simultaneous Cross-Dissolve without blank gap) -->
    <Transition name="page-crossfade">
      <!-- Step 1: Wedding Cover Home Page -->
      <WeddingCover
        v-if="currentPage === 'cover'"
        key="cover"
        :guest-name="guestName"
        @open-invitation="handleOpenInvitation"
        class="page-view"
      />

      <!-- Step 2: Save The Date Page matching Video -->
      <SaveTheDatePage
        v-else-if="currentPage === 'savethedate'"
        key="savethedate"
        @back-to-cover="handleBackToCover"
        class="page-view"
      />
    </Transition>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import WeddingCover from './components/WeddingCover.vue'
import SaveTheDatePage from './components/SaveTheDatePage.vue'

const guestName = ref('')
const currentPage = ref('cover') // 'cover' | 'savethedate'

function handleOpenInvitation() {
  currentPage.value = 'savethedate'
}

function handleBackToCover() {
  currentPage.value = 'cover'
}

onMounted(() => {
  // Parse URL query parameter ?guest=...
  const urlParams = new URLSearchParams(window.location.search)
  const guestParam = urlParams.get('guest')
  if (guestParam) {
    guestName.value = guestParam
  }
})
</script>

<style scoped>
.app-layout {
  width: 100vw;
  height: 100vh;
  height: 100dvh;
  position: relative;
  overflow: hidden;
  background-color: #0b132b;
}

.page-view {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
}

/* Seamless Continuous Cross-Fade: incoming page fades in over outgoing page */
.page-crossfade-enter-active {
  transition: opacity 0.85s cubic-bezier(0.25, 1, 0.5, 1), transform 0.85s cubic-bezier(0.25, 1, 0.5, 1);
  z-index: 2;
}

.page-crossfade-leave-active {
  transition: opacity 0.85s cubic-bezier(0.25, 1, 0.5, 1);
  z-index: 1;
}

.page-crossfade-enter-from {
  opacity: 0;
  transform: scale(1.03);
}

.page-crossfade-leave-to {
  opacity: 0;
}
</style>

