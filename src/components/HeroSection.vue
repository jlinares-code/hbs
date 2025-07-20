<template>
  <section class="animate__animated animate__fadeIn">
    <h1>¡Feliz Cumpleaños, Estrellita!</h1>
    <button @click="$emit('verPack')">Abrir mi regalo</button>
  </section>
</template>

<style scoped>
section {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  padding: 2rem 1rem;
  background: #000000cc;
  color: #ffffff;
  border-radius: 12px;
  box-shadow: 0 0 10px rgba(0,0,0,0.4);
  margin: 2rem auto;
  max-width: 600px;
  width: 100%;
  box-sizing: border-box;
  text-align: center;
}

h1 {
  font-size: 1.8rem;
  line-height: 1.3;
  margin-bottom: 1.5rem;
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