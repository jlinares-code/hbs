<template>
  <div class="gift-card animate__animated" :class="mostrar ? 'animate__flipInY' : ''" @click="mostrar = !mostrar">
    <img v-if="!mostrar" src="/regalo.png" alt="Regalo" />
    <div v-else class="reveal">
      <p>{{ item.descripcion }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['item'],
  data() {
    return { mostrar: false }
  }
}
</script>

<style scoped>
html,
body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
  height: 100%;
}

.gift-card {
  width: 90vw;
  max-width: 300px;
  height: 90vw;
  max-height: 300px;
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 0 12px rgba(0,0,0,0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  overflow: hidden;
  transition: transform 0.3s ease;
  margin: auto;
}

.gift-card:hover {
  transform: scale(1.05);
}

.gift-card img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.reveal {
  font-size: 0.9rem;
  color: #000;
  text-align: center;
  padding: 0.5rem;
  word-wrap: break-word;
}
</style>