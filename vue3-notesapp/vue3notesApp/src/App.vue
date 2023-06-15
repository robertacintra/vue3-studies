<script setup>
  import {ref} from "vue";

  const showModal = ref(false);
  const newNote = ref("");
  const errorMessage = ref("");
  const notes = ref([]);

  function getRandomColor(){
    return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
  }

  const addNote = () => {
    if(newNote.value.length < 10) {
      errorMessage.value = "Note needs to be 10 characters or more";
      return;
    }
    notes.value.push({
      id: Math.floor(Math.random() * 1000000),
      text: newNote.value,
      date: new Date(),
      backgroundColor: getRandomColor()
    });
    showModal.value = false;
    newNote.value = "";
    errorMessage.value = "";
  }
</script>

<template>
  <main>
    <div v-if="showModal" class="overlay">
      <div class="modal">
        <span @click="showModal = false" class="close"></span>
        <textarea v-model.trim="newNote" name="note" id="note" cols="30" rows="10"></textarea>
        <p v-if="errorMessage">{{ errorMessage }}</p>
        <button @click="addNote">Add note</button>
        
      </div>
    </div>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button @click="showModal = true">+</button>
      </header>
      <div class="cards-container">
        <div 
          v-for="note in notes" 
          :key="note.id"
          class="card" 
          :style="{backgroundColor: note.backgroundColor}"
        >
          <p class="main-text">{{ note.text }}</p>
          <p class="date">{{ note.date.toLocaleDateString("pt-BR") }}</p>
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
    color: white;
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
    font-weight: bold;
  }
  .date {
    font-size: 12px;
    color: rgb(66, 66, 66);
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
    background-color: transparent;
    border-radius: 10px;
    padding: 20px;
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
  textarea {
    width: 100%;
    height: 200px;
    padding: 5px;
    font-size: 20px;
  }
  .modal .close {
    cursor: pointer;
    padding: 2px;
  }
  .close:after, .close:before {
    content: "";
    height: 20px;
    width: 20px;
    border-top: 1px solid rgb(190, 5, 5);
    position: absolute;
    top: 7px;
    right: -8px;
    -moz-transform: rotate(-45deg);
    -ms-transform: rotate(-45deg);
    -webkit-transform: rotate(-45deg);
    transform: rotate(-45deg);
  }
  .close:before {
    right: 6px;
    -moz-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    -webkit-transform: rotate(45deg);
    transform: rotate(45deg);
  }
  .close:hover {
    opacity: 0.7;
  }
  
  .modal p {
    color: rgb(230, 13, 13);
    font-size: 14px;
    font-weight: bold;
  }
</style>