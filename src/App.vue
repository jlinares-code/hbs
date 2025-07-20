<template>
  <div :class="['app', directionClass]">
    <transition name="slide" mode="out-in">
      <component :is="currentComponent" :key="currentPage" @verPack="nextPage('right')" @continuar="nextPage('left')"
        :regalos="regalos" />
    </transition>
    <div class="background-image" />
  </div>
</template>

<script>
import HeroSection from './components/HeroSection.vue'
import FirstGift from './components/FirstGift.vue'
import PackSection from './components/PackSection.vue'
import MessageSection from './components/MessageSection.vue'

export default {
  components: { HeroSection, FirstGift, PackSection, MessageSection },
  data() {
    return {
      currentPage: 0,
      direction: 'right',
      regalos: [
        { descripcion: 'Una turbo abuela 👩‍🦳' },
        { descripcion: 'Unas garritas 😼' }
      ]
    }
  },
  computed: {
    currentComponent() {
      return [HeroSection, FirstGift, PackSection, MessageSection][this.currentPage]
    },
    directionClass() {
      return this.direction === 'right' ? 'slide-right' : 'slide-left'
    }
  },
  methods: {
    nextPage(direction = 'right') {
      this.direction = direction
      if (this.currentPage < 3) this.currentPage++
    }
  }
}
</script>

<style>
@import 'animate.css';

body,
html {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
  height: 100%;
}

:root {
  background: linear-gradient(to bottom, #000000, #1e3a8a);
}

.app {
  position: relative;
  min-height: 100vh;
  overflow-x: hidden;
  font-family: 'Quicksand', sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 2rem 1rem;
  /* background-color: #000; Fallback color */
}

/* Fondo animado solo una vez */
.background-image {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-image: url('/fondo.png');
  /* cambia por tu imagen */
  background-size: cover;
  background-position: 20% center;
  background-repeat: no-repeat;
  opacity: 0.1;
  z-index: -1;
  animation: scroll-horizontal-once 0.5s ease-out 1;
}

@keyframes scroll-horizontal-once {
  0% {
    transform: translateX(-100%);
  }

  /* 50%{
    transform: translateX(100%);
  } */
  100% {
    transform: translateX(0);
  }
}
</style>

<!-- /* background: linear-gradient(to bottom, #000000, #1e3a8a); */ -->