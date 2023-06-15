<script setup>
  import {ref} from "vue";

  const showModal = ref(false);
</script>

<template>
  <main>
    <div v-if="showModal" class="overlay">
      <div class="modal">
        <textarea name="note" id="note" cols="30" rows="10"></textarea>
        <button>Add note</button>
        <button @click="showModal = false" class="close">Close</button>
      </div>
    </div>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button @click="showModal = true">+</button>
      </header>
      <div class="cards-container">
        <div class="card">
          <p class="main-text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Quasi esse delectus voluptate? Assumenda magnam illum hic!</p>
          <p class="date">14/06/23</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
  main {
    height: 100vh;
    width: 100vw;
  }
  .container{
    max-width: 1000px;
    padding: 10px;
    margin: 0 auto;
  }
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  h1 {
    font-weight: bold;
    margin-bottom: 25px;
    font-size: 65px;
  }
  header button {
    border: none;
    padding: 10px;
    width: 50px;
    height: 50px;
    cursor: pointer;
    background-color: rgba(42, 190, 5, 0.432);
    color: white;
    font-size: 20px;
    border-radius: 100%;
  }
  .card {
    width: 225px;
    height: 225px;
    background-color: rgb(255, 255, 119);
    padding: 10px;
    border-radius: 15px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    margin-right: 20px;
    margin-bottom: 20px;
  }
  .main-text {
    color: black;
    font-size: 14px;
    line-height: 1.25;
  }
  .date {
    font-size: 12px;
    font-weight: bold;
    color: rgb(199, 199, 199);
    margin-top: auto;
  }
  .cards-container {
    display: flex;
    flex-wrap: wrap;
  }
  .overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.77);
    transform: translate(-50%, -50%);
    top: 50%;
    left: 50%;
    display: flex;
    z-index: 10;
    align-items: center;
    justify-content: center;
  }
  .modal {
    width: 750px;
    background-color: white;
    border-radius: 10px;
    padding: 30px;
    position: relative;
    display: flex;
    flex-direction: column;
  }
  .modal button {
    padding: 10px 20px;
    font-size: 20px;
    width: 100%;
    background-color: blueviolet;
    border: none;
    color: white;
    cursor: pointer;
    margin-top: 15px;
  }
  .modal p {
    margin-left: auto;
    font-size: 20px;
    z-index: 100000;
    cursor: pointer;
  }
  textarea {
    width: 100%;
    height: 200px;
    padding: 5px;
    font-size: 20px;
  }
  .modal .close {
    background-color: rgb(190, 5, 5);
    margin-top: 7px;
  }
</style>