<template>
  <section class="animate__animated animate__fadeInUp">
    <h2>Primera parte de tu regalo 🎁</h2>
    <transition-group name="reveal" tag="div" class="pack">
      <img v-if="mostrar" key="trago" src="/trago.png" alt="Trago" class="item" />
      <img v-if="mostrar" key="torta" src="/torta.png" alt="Torta" class="item" />
    </transition-group>
    <button v-if="!mostrar" @click="mostrar = true">Revelar regalo</button>
    <button v-if="mostrar" @click="$emit('continuar')">Ver más sorpresas</button>
  </section>
</template>

<script>
export default {
  data() {
    return {
      mostrar: false
    }
  }
}
</script>

<style scoped>
section {
  padding: 2rem 1rem;
}
.pack {
  display: flex;
  justify-content: center;
  gap: 2rem;
  margin: 2rem 0;
}
.item {
  width: 140px;
  border-radius: 12px;
  box-shadow: 0 0 10px rgba(0,0,0,0.4);
  transition: transform 0.3s;
}
.item:hover {
  transform: scale(1.05);
}
button {
  background: #ef4444;
  border: none;
  padding: 0.75rem 1.5rem;
  color: white;
  font-size: 1rem;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.3s ease;
  margin-top: 1rem;
}
button:hover {
  background: #1e3a8a;
}
.reveal-enter-active, .reveal-leave-active {
  transition: all 0.8s ease;
}
.reveal-enter-from {
  opacity: 0;
  transform: scale(0.8);
}
.reveal-enter-to {
  opacity: 1;
  transform: scale(1);
}
</style>