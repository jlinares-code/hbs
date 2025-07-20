<template>
  <div class="app" :class="directionClass">
    <transition name="slide" mode="out-in">
      <component
        :is="currentComponent"
        :key="currentPage"
        @verPack="nextPage('right')"
        @continuar="nextPage('left')"
        :regalos="regalos"
      />
    </transition>
    <div
      class="background-image"
      :key="backgroundKey"
      :style="backgroundStyle"
    />
  </div>
</template>

<script>
import HeroSection from './components/HeroSection.vue'
import FirstGift from './components/FirstGift.vue'
import PackSection from './components/PackSection.vue'
import MessageSection from './components/MessageSection.vue'

export default {
  components: {
    HeroSection,
    FirstGift,
    PackSection,
    MessageSection
  },
  data() {
    return {
      currentPage: 0,
      direction: 'right',
      backgroundKey: 0, // clave para forzar el re-render del fondo
      regalos: [
        { descripcion: 'Una turbo abuela 👩‍🦳' },
        { descripcion: 'Unas garritas 😼, para este perro frio' }
      ],
      backgrounds: [
        '1fondoTest.png',
        'fondo.png',
        'fondo3.png',
        'fondo4.png'
      ],
      backgroundAnimations: [
        'scroll-horizontal-once 0.5s ease-out 1',
        'scroll-horizontal-once 1s ease-in-out 1',
        'scroll-horizontal-once 0.7s ease-in 1',
        'scroll-horizontal-once 0.8s ease-out 1'
      ]
    }
  },
  computed: {
    currentComponent() {
      return [
        HeroSection,
        FirstGift,
        PackSection,
        MessageSection
      ][this.currentPage]
    },
    directionClass() {
      return this.direction === 'right' ? 'slide-right' : 'slide-left'
    },
    backgroundStyle() {
      const imageUrl = this.backgrounds[this.currentPage]
      return {
        backgroundImage: `url('${imageUrl}')`,
        animation: this.backgroundAnimations[this.currentPage]
      }
    }
  },
  methods: {
    nextPage(direction = 'right') {
      this.direction = direction
      if (this.currentPage < 3) {
        this.currentPage++

        // Reiniciar animación del fondo forzando key diferente
        this.backgroundKey++ // obliga al div a renderizarse de nuevo
      }
    }
  }
}
</script>

<style>
@import 'animate.css';
:root {
  background: linear-gradient(to bottom, #000000, #1e3a8a);
}

html,
body {
  margin: 0;
  padding: 0;
  height: 100%;
  overflow: hidden;
}

.app {
  position: relative;
  min-height: 100vh;
  overflow: hidden;
  font-family: 'Quicksand', sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem 1rem;
}

/* Fondo por página */
.background-image {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  opacity: 0.2;
  z-index: -1;
}

/* Animación de fondo */
@keyframes scroll-horizontal-once {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(0);
  }
}
</style>




<!-- /* background: linear-gradient(to bottom, #000000, #1e3a8a); */ -->