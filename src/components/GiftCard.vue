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
.gift-card {
  width: 100px;
  height: 100px;
  background: transparent;
  border-radius: 12px;
  box-shadow: 0 0 12px rgba(0,0,0,0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  padding: 0.5rem;
  transition: transform 0.3s ease;
}
.gift-card:hover {
  transform: scale(1.05);
}
.reveal {
  font-size: 0.75rem;
  color: #fff;
  text-align: center;
}
img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  }
</style>