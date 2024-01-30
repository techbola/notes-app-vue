<script setup>
  import {ref} from "vue";

  const showModal = ref(false);
  const note = ref("");
  const notes = ref([]);
  const errorMsg = ref("");

  const closeModal = () => {
    showModal.value = false;
    note.value = "";
  }

  const addNote = () => {
    if (validateInput()) {
      const newNote = {
        id: Math.floor(Math.random() * 1000000),
        text: note.value,
        date: new Date(),
        bgColor: generateColor()
      };
      notes.value.push(newNote);
      closeModal();
    }
  }

  const generateColor = () => {
    return "hsl(" + Math.random() * 360 + ", 100%, 75%)"
  }

  const validateInput = () => {
    if (note.value.length < 10) {
      errorMsg.value = "Note needs to be 10 characters or more!";
      return false;
    }
    errorMsg.value = "";
    return true;
  }
</script>

<template>
  <main>
    <div v-if="showModal" class="overlay">
      <div class="modal">
        <textarea 
          name="note" 
          id="note" 
          cols="30" 
          rows="10"
          v-model.trim="note"
        ></textarea>

        <p v-if="errorMsg" class="error">{{ errorMsg }}</p>

        <div class="actions">
          <button @click="closeModal" class="close-modal">Close</button>
          <button @click="addNote" class="add-note-button">Add Note</button>
        </div>
      </div>
    </div>

    <div class="container">
      <header>
        <h1>Notes</h1>
        <button @click="showModal = true">+</button>
      </header>
      <div class="cards-container">
        <div 
          class="card" v-for="note in notes" 
          :key="note.id"
          :style="{backgroundColor: note.bgColor}"
        >
          <p class="main-text">{{ note.text }}</p>
          <p class="date">{{ note.date.toLocaleDateString("en-US") }}</p>
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

  .container {
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
    font-size: 75px;
  }

  header button {
    border: none;
    padding: 10px;
    width: 50px;
    height: 50px;
    cursor: pointer;
    background-color: rgb(21, 20, 20);
    border-radius: 100%;
    font-size: 20px;
    color: white;
  }

  .card {
    width: 225px;
    height: 225px;
    background-color: rgb(237, 182, 44);
    padding: 10px;
    border-radius: 15px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .date {
    font-size: 12px;
    font-weight: bold;
  }

  .cards-container {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
  }

  .overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.7);
    display: flex;
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

  .modal .actions {
    margin-top: 24px;
    display: flex;
    gap: 10px;
    justify-content: end;
  }

  .modal button {
    border-radius: 10px;
    padding: 10px 20px;
    font-size: 20px;
    cursor: pointer;
    color: white;
  }

  .add-note-button {
    background-color: blueviolet;
  }

  .close-modal {
    background-color: rgb(193, 15, 15);
  }

  .error {
    color: rgb(193, 15, 15);
  }
</style>
