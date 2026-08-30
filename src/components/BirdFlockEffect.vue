<template>
  <div class="bird-scene-container" :class="{ 'is-active': active }" aria-hidden="true">
    <!-- Bird 1: Lead Forefront Glider -->
    <div class="bird-container bird-container--1">
      <div class="bird bird--lead">
        <LottieBluebird :speed="1.2" :flipForward="true" />
        <div class="bird-stardust"></div>
      </div>
    </div>

    <!-- Bird 2: Close Follower -->
    <div class="bird-container bird-container--2">
      <div class="bird bird--follower">
        <LottieBluebird :speed="1.05" :flipForward="true" />
        <div class="bird-stardust"></div>
      </div>
    </div>

    <!-- Bird 3: High Sky Soarer -->
    <div class="bird-container bird-container--3">
      <div class="bird bird--high">
        <LottieBluebird :speed="1.15" :flipForward="true" />
        <div class="bird-stardust"></div>
      </div>
    </div>

    <!-- Bird 4: Graceful Mid-Sky Glider -->
    <div class="bird-container bird-container--4">
      <div class="bird bird--fast">
        <LottieBluebird :speed="1.25" :flipForward="true" />
        <div class="bird-stardust"></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import LottieBluebird from './LottieBluebird.vue'

defineProps({
  active: {
    type: Boolean,
    default: false
  }
})
</script>

<style lang="scss" scoped>
// ==========================================
// SCSS Variables & Natural Flight Parameters
// ==========================================
$stardust-gold: rgba(254, 240, 138, 0.85);
$stardust-blue: rgba(147, 197, 253, 0.6);

.bird-scene-container {
  position: absolute;
  inset: 0;
  pointer-events: none;
  overflow: hidden;
  z-index: 25;
}

// Bird Containers with Hardware Accelerated GPU 3D Keyframe Flight
.bird-container {
  position: absolute;
  left: -15%;
  will-change: transform, opacity;
  pointer-events: none;

  &--1 {
    top: 15%;
    animation: flight-curve-1 11s linear infinite;
    animation-delay: 0s;
  }

  &--2 {
    top: 24%;
    animation: flight-curve-2 12s linear infinite;
    animation-delay: 2.2s;
  }

  &--3 {
    top: 10%;
    animation: flight-curve-3 13s linear infinite;
    animation-delay: 5s;
  }

  &--4 {
    top: 32%;
    animation: flight-curve-4 10s linear infinite;
    animation-delay: 7.5s;
  }
}

// Bird Body Sizes & Stardust
.bird {
  position: relative;
  will-change: transform;

  &--lead {
    width: 82px;
    height: 82px;
  }

  &--follower {
    width: 74px;
    height: 74px;
  }

  &--high {
    width: 65px;
    height: 65px;
  }

  &--fast {
    width: 78px;
    height: 78px;
  }

  &--mid {
    width: 70px;
    height: 70px;
  }

  &--distant {
    width: 54px;
    height: 54px;
    opacity: 0.85;
  }

  &--horizon {
    width: 72px;
    height: 72px;
  }

  .bird-stardust {
    position: absolute;
    bottom: 14%;
    left: 8%;
    width: 14px;
    height: 14px;
    background: radial-gradient(circle, $stardust-gold 0%, $stardust-blue 45%, transparent 70%);
    filter: blur(1px);
    animation: stardust-twinkle 0.45s ease-out infinite alternate;
  }
}

@keyframes stardust-twinkle {
  0% {
    opacity: 0.25;
    transform: scale(0.5);
  }
  100% {
    opacity: 0.95;
    transform: scale(1.3);
  }
}

// ==========================================
// SCSS Dynamic Flight Paths
// ==========================================

// Flight Path 1: Smooth Climbing & Dipping Wave
@keyframes flight-curve-1 {
  0% {
    transform: scale(0.35) translate3d(-10vw, 0vh, 0);
    opacity: 0;
  }
  4% {
    opacity: 1;
    transform: scale(0.48) translate3d(2vw, 1.5vh, 0);
  }
  18% {
    transform: scale(0.65) translate3d(22vw, 3.5vh, 0) rotate(-3deg);
  }
  35% {
    transform: scale(0.85) translate3d(46vw, -1.5vh, 0) rotate(3deg);
  }
  52% {
    transform: scale(0.92) translate3d(70vw, 2.5vh, 0) rotate(-2deg);
  }
  70% {
    transform: scale(0.92) translate3d(94vw, -0.5vh, 0) rotate(1deg);
    opacity: 1;
  }
  80% {
    transform: scale(0.92) translate3d(112vw, 0vh, 0) rotate(0deg);
    opacity: 0.95;
  }
  88% {
    transform: scale(0.92) translate3d(120vw, 0vh, 0);
    opacity: 0;
  }
  100% {
    transform: scale(0.92) translate3d(120vw, 0vh, 0);
    opacity: 0;
  }
}

// Flight Path 2: Harmonic Swoop with Mid-Altitude Bank
@keyframes flight-curve-2 {
  0% {
    transform: scale(0.38) translate3d(-10vw, -2vh, 0);
    opacity: 0;
  }
  4% {
    opacity: 1;
    transform: scale(0.5) translate3d(3vw, 0vh, 0);
  }
  22% {
    transform: scale(0.72) translate3d(28vw, -4vh, 0) rotate(4deg);
  }
  42% {
    transform: scale(0.8) translate3d(56vw, 2vh, 0) rotate(-3deg);
  }
  62% {
    transform: scale(0.82) translate3d(82vw, -2vh, 0) rotate(2deg);
  }
  78% {
    transform: scale(0.82) translate3d(108vw, 0vh, 0) rotate(0deg);
    opacity: 1;
  }
  86% {
    transform: scale(0.82) translate3d(120vw, 0vh, 0);
    opacity: 0;
  }
  100% {
    transform: scale(0.82) translate3d(120vw, 0vh, 0);
    opacity: 0;
  }
}

// Flight Path 3: High Sky Glide Across Upper Clouds
@keyframes flight-curve-3 {
  0% {
    transform: scale(0.3) translate3d(-10vw, 2vh, 0);
    opacity: 0;
  }
  5% {
    opacity: 1;
    transform: scale(0.42) translate3d(4vw, 0.5vh, 0);
  }
  25% {
    transform: scale(0.62) translate3d(30vw, -2vh, 0) rotate(3deg);
  }
  50% {
    transform: scale(0.75) translate3d(62vw, 2vh, 0) rotate(-2.5deg);
  }
  72% {
    transform: scale(0.75) translate3d(92vw, -1.5vh, 0) rotate(1.5deg);
    opacity: 1;
  }
  82% {
    transform: scale(0.75) translate3d(114vw, 0vh, 0);
    opacity: 0.95;
  }
  90% {
    opacity: 0;
    transform: scale(0.75) translate3d(122vw, 0vh, 0);
  }
  100% {
    opacity: 0;
    transform: scale(0.75) translate3d(122vw, 0vh, 0);
  }
}

// Flight Path 4: Fast Lower Swoop
@keyframes flight-curve-4 {
  0% {
    transform: scale(0.35) translate3d(-10vw, 3vh, 0);
    opacity: 0;
  }
  5% {
    opacity: 1;
  }
  20% {
    transform: scale(0.68) translate3d(24vw, -3vh, 0) rotate(-4deg);
  }
  45% {
    transform: scale(0.88) translate3d(54vw, 4vh, 0) rotate(4deg);
  }
  70% {
    transform: scale(0.88) translate3d(88vw, -2vh, 0) rotate(-1deg);
    opacity: 1;
  }
  82% {
    transform: scale(0.88) translate3d(112vw, 0vh, 0);
    opacity: 0.95;
  }
  90% {
    opacity: 0;
    transform: scale(0.88) translate3d(120vw, 0vh, 0);
  }
  100% {
    opacity: 0;
    transform: scale(0.88) translate3d(120vw, 0vh, 0);
  }
}
</style>
