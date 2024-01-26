<script setup>

</script>

<template>
  <main>
    <div class="overlay">
      <div class="modal">
        <textarea name="note" id="note" cols="30" rows="10"></textarea>
        <div class="actions">
          <button class="close-modal">Close</button>
          <button class="add-note-button">Add Note</button>
        </div>
      </div>
    </div>

    <div class="container">
      <header>
        <h1>Notes</h1>
        <button>+</button>
      </header>
      <div class="cards-container">
        <div class="card">
          <p class="main-text">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Officiis, mollitia!
          </p>
          <p class="date">26/1/2024</p>
        </div>

        <div class="card">
          <p class="main-text">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Officiis, mollitia!
          </p>
          <p class="date">26/1/2024</p>
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
    background-color: red;
  }
</style>
