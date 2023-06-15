<script setup>
  import { ref } from "vue";
  const count = ref(0);

  const addToCount = () => {
    count.value = count.value + 1
  }

  const subFromCount = () => {
    count.value = count.value - 1
  }
</script>

<template>
  <main>
    <div>
      <h4>The current count is...</h4>
      <h1>
        {{ count }}
      </h1>
      <button @click="subFromCount">-</button>
      <button @click="addToCount">+</button>
    </div>
  </main>
</template>

<style scoped>
  main {
    background-color: aliceblue;
    height: 100vh;
    width: 100vw;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: monospace;
    font-size: 24px;
  }
  div {
    text-align: center;
  }
  button {
    background-color: rgba(255, 157, 211, 0.911);
    border: none;
    border-radius: 5px;
    margin: 1vw;
    min-width: 10vw;
    min-height: 5vh;
    font-size: 24px;
  }
</style>