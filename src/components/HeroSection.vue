<template>
  <section class="animate__animated animate__fadeIn">
    <h1>🎉 ¡Feliz Cumpleaños, Estrellita! 🎉</h1>
    <button @click="$emit('verPack')">Abrir mi regalo</button>
  </section>
</template>

<style scoped>
section {
  padding: 3rem 1rem;
  background: #000000;
  color: #ffffff;
  border-radius: 12px;
  box-shadow: 0 0 10px rgba(0,0,0,0.4);
  margin: 2rem auto;
  max-width: 600px;
}
button {
  padding: 0.75rem 1.5rem;
  background: #1e3a8a;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 1rem;
  transition: background 0.3s ease;
}
button:hover {
  background: #ef4444;
}
</style>