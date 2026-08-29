<template>
  <div class="customize-bar-container">
    <!-- Floating Trigger Pill -->
    <button
      class="customize-pill-btn"
      @click="isExpanded = !isExpanded"
      :title="isExpanded ? 'បិទផ្ទាំងកែសម្រួល' : 'កែសម្រួលឈ្មោះភ្ញៀវ & ចែករំលែក'"
    >
      <span class="pill-icon">✨</span>
      <span class="pill-text">{{ isExpanded ? 'បិទ (Close)' : 'កែឈ្មោះភ្ញៀវ (Guest Name)' }}</span>
    </button>

    <!-- Expanded Drawer / Panel -->
    <div v-if="isExpanded" class="customize-drawer">
      <div class="drawer-header">
        <h4>✨ កំណត់ឈ្មោះភ្ញៀវកិត្តិយស</h4>
        <button class="drawer-close-btn" @click="isExpanded = false">✕</button>
      </div>

      <div class="drawer-content">
        <label class="input-label">បញ្ចូលឈ្មោះភ្ញៀវសម្រាប់តំណភ្ជាប់ (Guest Name):</label>
        <div class="input-group">
          <input
            v-model="nameInput"
            @input="updateGuestName"
            type="text"
            placeholder="ឧទាហរណ៍៖ ឯកឧត្តម លោកជំទាវ..."
            class="guest-input"
          />
        </div>

        <!-- Quick Title Presets -->
        <div class="preset-chips">
          <button
            v-for="preset in presets"
            :key="preset"
            class="preset-chip"
            @click="applyPreset(preset)"
          >
            {{ preset }}
          </button>
        </div>

        <!-- Share & Copy Link -->
        <div class="share-group">
          <button class="copy-link-btn" @click="copyShareLink">
            <span v-if="copied">✅ បានចម្លងតំណភ្ជាប់ (Link Copied!)</span>
            <span v-else>🔗 ចម្លង Link ផ្ញើទៅកាន់ភ្ញៀវ (Copy Link)</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
  modelValue: {
    type: String,
    default: ''
  }
})

const emit = defineEmits(['update:modelValue'])

const isExpanded = ref(false)
const nameInput = ref(props.modelValue || 'ឯកឧត្តម លោកជំទាវ')
const copied = ref(false)

const presets = [
  'ឯកឧត្តម & លោកជំទាវ',
  'លោក & លោកស្រី',
  'អ្នកនាង & កញ្ញា',
  'មិត្តភក្តិជិតស្និទ្ធ'
]

function updateGuestName() {
  emit('update:modelValue', nameInput.value)
}

function applyPreset(text) {
  nameInput.value = text
  updateGuestName()
}

async function copyShareLink() {
  const url = new URL(window.location.href)
  if (nameInput.value) {
    url.searchParams.set('guest', nameInput.value)
  } else {
    url.searchParams.delete('guest')
  }

  try {
    await navigator.clipboard.writeText(url.toString())
    copied.value = true
    setTimeout(() => {
      copied.value = false
    }, 2500)
  } catch (e) {
    prompt('ចម្លង Link នេះ:', url.toString())
  }
}
</script>

<style scoped>
.customize-bar-container {
  position: fixed;
  bottom: 18px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 90;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.customize-pill-btn {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px 18px;
  background: rgba(15, 23, 42, 0.85);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border: 1px solid rgba(212, 175, 55, 0.5);
  border-radius: 24px;
  color: #f8fafc;
  font-family: var(--font-body);
  font-size: 0.82rem;
  font-weight: 600;
  cursor: pointer;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.35);
  transition: all 0.3s ease;
}

.customize-pill-btn:hover {
  transform: translateY(-2px);
  background: rgba(30, 58, 138, 0.95);
  border-color: rgba(212, 175, 55, 0.9);
  box-shadow: 0 6px 20px rgba(37, 99, 235, 0.4);
}

.pill-icon {
  font-size: 0.9rem;
}

/* Drawer */
.customize-drawer {
  position: absolute;
  bottom: 48px;
  width: 320px;
  background: rgba(15, 23, 42, 0.95);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border: 1.5px solid rgba(212, 175, 55, 0.6);
  border-radius: 18px;
  padding: 16px;
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.6);
  animation: slideUp 0.3s cubic-bezier(0.16, 1, 0.3, 1);
  color: #f1f5f9;
}

.drawer-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 12px;
}

.drawer-header h4 {
  font-size: 0.9rem;
  color: #fef08a;
  font-weight: 700;
}

.drawer-close-btn {
  background: transparent;
  border: none;
  color: #94a3b8;
  font-size: 0.9rem;
  cursor: pointer;
}

.drawer-content {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.input-label {
  font-size: 0.75rem;
  color: #cbd5e1;
}

.guest-input {
  width: 100%;
  padding: 8px 12px;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 8px;
  color: #ffffff;
  font-size: 0.88rem;
  outline: none;
  font-family: inherit;
}

.guest-input:focus {
  border-color: #3b82f6;
  background: rgba(255, 255, 255, 0.15);
}

.preset-chips {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}

.preset-chip {
  padding: 4px 8px;
  background: rgba(37, 99, 235, 0.25);
  border: 1px solid rgba(96, 165, 250, 0.4);
  border-radius: 12px;
  color: #bfdbfe;
  font-size: 0.72rem;
  cursor: pointer;
  transition: all 0.2s;
}

.preset-chip:hover {
  background: rgba(37, 99, 235, 0.5);
  color: #ffffff;
}

.copy-link-btn {
  width: 100%;
  padding: 8px;
  background: linear-gradient(135deg, #1e40af, #2563eb);
  color: #ffffff;
  border: none;
  border-radius: 8px;
  font-size: 0.8rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
  box-shadow: 0 4px 10px rgba(37, 99, 235, 0.3);
}

.copy-link-btn:hover {
  background: linear-gradient(135deg, #2563eb, #3b82f6);
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(12px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
