<template>
  <div class="bird-scene-container" :class="{ 'is-active': active }" aria-hidden="true">
    <!-- Bird 1: Lead Forefront Glider -->
    <div class="bird-container bird-container--1">
      <div class="bird bird--lead">
        <LottieBluebird :speed="1.25" :flipForward="true" />
        <div class="bird-stardust"></div>
      </div>
    </div>

    <!-- Bird 2: Close Follower / Wingmate -->
    <div class="bird-container bird-container--2">
      <div class="bird bird--follower">
        <LottieBluebird :speed="1.15" :flipForward="true" />
        <div class="bird-stardust"></div>
      </div>
    </div>

    <!-- Bird 3: High Sky Soarer -->
    <div class="bird-container bird-container--3">
      <div class="bird bird--high">
        <LottieBluebird :speed="1.0" :flipForward="true" />
        <div class="bird-stardust"></div>
      </div>
    </div>

    <!-- Bird 4: Fast Swooping Swallow -->
    <div class="bird-container bird-container--4">
      <div class="bird bird--fast">
        <LottieBluebird :speed="1.35" :flipForward="true" />
        <div class="bird-stardust"></div>
      </div>
    </div>

    <!-- Bird 5: Mid-Sky Crossing Glider -->
    <div class="bird-container bird-container--5">
      <div class="bird bird--mid">
        <LottieBluebird :speed="1.1" :flipForward="true" />
        <div class="bird-stardust"></div>
      </div>
    </div>

    <!-- Bird 6: Distant Soft Soarer -->
    <div class="bird-container bird-container--6">
      <div class="bird bird--distant">
        <LottieBluebird :speed="0.95" :flipForward="true" />
        <div class="bird-stardust"></div>
      </div>
    </div>

    <!-- Bird 7: Horizon Wave Leader -->
    <div class="bird-container bird-container--7">
      <div class="bird bird--horizon">
        <LottieBluebird :speed="1.2" :flipForward="true" />
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

// Bird Containers (Flight Trajectories with Staggered Delays for Continuous Sky Flight)
.bird-container {
  position: absolute;
  left: -15%;
  transform: scale(0) translateX(-10vw);
  will-change: transform, opacity;
  pointer-events: none;

  &--1 {
    top: 20%;
    animation: flight-curve-1 10.5s linear infinite;
    animation-delay: 0s;
  }

  &--2 {
    top: 28%;
    animation: flight-curve-2 11.5s linear infinite;
    animation-delay: 1.2s;
  }

  &--3 {
    top: 10%;
    animation: flight-curve-3 12.5s linear infinite;
    animation-delay: 3s;
  }

  &--4 {
    top: 38%;
    animation: flight-curve-4 9.5s linear infinite;
    animation-delay: 4.8s;
  }

  &--5 {
    top: 18%;
    animation: flight-curve-1 11s linear infinite;
    animation-delay: 6.5s;
  }

  &--6 {
    top: 48%;
    animation: flight-curve-2 13s linear infinite;
    animation-delay: 8s;
  }

  &--7 {
    top: 14%;
    animation: flight-curve-3 10.8s linear infinite;
    animation-delay: 9.6s;
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
    transform: scale(0.35) translateX(-10vw) translateY(0vh);
    opacity: 0;
  }
  4% {
    opacity: 1;
    transform: scale(0.48) translateX(2vw) translateY(1.5vh);
  }
  18% {
    transform: scale(0.65) translateX(22vw) translateY(3.5vh) rotate(-3deg);
  }
  35% {
    transform: scale(0.85) translateX(46vw) translateY(-1.5vh) rotate(3deg);
  }
  52% {
    transform: scale(0.92) translateX(70vw) translateY(2.5vh) rotate(-2deg);
  }
  70% {
    transform: scale(0.92) translateX(94vw) translateY(-0.5vh) rotate(1deg);
    opacity: 1;
  }
  80% {
    transform: scale(0.92) translateX(112vw) translateY(0vh) rotate(0deg);
    opacity: 0.95;
  }
  88% {
    transform: scale(0.92) translateX(120vw) translateY(0vh);
    opacity: 0;
  }
  100% {
    transform: scale(0.92) translateX(120vw) translateY(0vh);
    opacity: 0;
  }
}

// Flight Path 2: Harmonic Swoop with Mid-Altitude Bank
@keyframes flight-curve-2 {
  0% {
    transform: scale(0.38) translateX(-10vw) translateY(-2vh);
    opacity: 0;
  }
  4% {
    opacity: 1;
    transform: scale(0.5) translateX(3vw) translateY(0vh);
  }
  22% {
    transform: scale(0.72) translateX(28vw) translateY(-4vh) rotate(4deg);
  }
  42% {
    transform: scale(0.8) translateX(56vw) translateY(2vh) rotate(-3deg);
  }
  62% {
    transform: scale(0.82) translateX(82vw) translateY(-2vh) rotate(2deg);
  }
  78% {
    transform: scale(0.82) translateX(108vw) translateY(0vh) rotate(0deg);
    opacity: 1;
  }
  86% {
    transform: scale(0.82) translateX(120vw) translateY(0vh);
    opacity: 0;
  }
  100% {
    transform: scale(0.82) translateX(120vw) translateY(0vh);
    opacity: 0;
  }
}

// Flight Path 3: High Sky Glide Across Upper Clouds
@keyframes flight-curve-3 {
  0% {
    transform: scale(0.3) translateX(-10vw) translateY(2vh);
    opacity: 0;
  }
  5% {
    opacity: 1;
    transform: scale(0.42) translateX(4vw) translateY(0.5vh);
  }
  25% {
    transform: scale(0.62) translateX(30vw) translateY(-2vh) rotate(3deg);
  }
  50% {
    transform: scale(0.75) translateX(62vw) translateY(2vh) rotate(-2.5deg);
  }
  72% {
    transform: scale(0.75) translateX(92vw) translateY(-1.5vh) rotate(1.5deg);
    opacity: 1;
  }
  82% {
    transform: scale(0.75) translateX(114vw) translateY(0vh);
    opacity: 0.95;
  }
  90% {
    opacity: 0;
    transform: scale(0.75) translateX(122vw) translateY(0vh);
  }
  100% {
    opacity: 0;
    transform: scale(0.75) translateX(122vw) translateY(0vh);
  }
}

// Flight Path 4: Fast Lower Swoop
@keyframes flight-curve-4 {
  0% {
    transform: scale(0.35) translateX(-10vw) translateY(3vh);
    opacity: 0;
  }
  5% {
    opacity: 1;
  }
  20% {
    transform: scale(0.68) translateX(24vw) translateY(-3vh) rotate(-4deg);
  }
  45% {
    transform: scale(0.88) translateX(54vw) translateY(4vh) rotate(4deg);
  }
  70% {
    transform: scale(0.88) translateX(88vw) translateY(-2vh) rotate(-1deg);
    opacity: 1;
  }
  82% {
    transform: scale(0.88) translateX(112vw) translateY(0vh);
    opacity: 0.95;
  }
  90% {
    opacity: 0;
    transform: scale(0.88) translateX(120vw) translateY(0vh);
  }
  100% {
    opacity: 0;
    transform: scale(0.88) translateX(120vw) translateY(0vh);
  }
}
</style>
