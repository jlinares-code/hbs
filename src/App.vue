<template>
  <div class="app">
    <HeroSection @verPack="verPack" />
    <FirstGift v-if="mostrarPrimeraParte" @continuar="mostrarSegundaParte = true" />
    <PackSection v-if="mostrarSegundaParte" :regalos="regalos" />
    <MessageSection v-if="mostrarSegundaParte" />
  </div>
</template>

<script>
import HeroSection from './components/HeroSection.vue'
import FirstGift from './components/FirstGift.vue'
import PackSection from './components/PackSection.vue'
import MessageSection from './components/MessageSection.vue'
import confetti from 'canvas-confetti'

export default {
  components: { HeroSection, FirstGift, PackSection, MessageSection },
  data() {
    return {
      mostrarPrimeraParte: false,
      mostrarSegundaParte: false,
      regalos: [
        { descripcion: 'Una turbo abuela 👩‍🦳' },
        { descripcion: 'Unas garritas 😼' }
      ]
    }
  },
  methods: {
    verPack() {
      this.mostrarPrimeraParte = true
      this.dispararConfetti()
    },
    dispararConfetti() {
      confetti({
        particleCount: 200,
        spread: 120,
        origin: { y: 0.6 },
        colors: ['#1e3a8a', '#ef4444', '#000000']
      })
    }
  }
}
</script>

<style>
@import 'animate.css';

body {
  font-family: 'Quicksand', sans-serif;
  background: linear-gradient(to bottom, #000000, #1e3a8a);
  margin: 0;
  color: #ffffff;
}
.app {
  text-align: center;
  padding: 1rem;
}
</style>