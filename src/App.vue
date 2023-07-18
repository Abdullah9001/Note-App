<script setup>
import { Icon } from "@iconify/vue";
import { ref } from "vue";

const showModal = ref(false);
const newNote = ref("");
const errMessage = ref("");
const notes = ref([]);

function getDarkColor() {
  let color = "#";
  for (let i = 0; i < 6; i++) {
    color += Math.floor(Math.random() * 10);
  }
  return color;
}

const addNote = () => {
  if (newNote.value.length < 10) {
    return (errMessage.value = "Note needs to be 10 characters or more!");
  }
  notes.value.push({
    id: Math.floor(Math.random() * 1000000),
    text: newNote.value,
    date: new Date().toLocaleDateString("en-US"),
    backgroundColor: getDarkColor(),
  });

  showModal.value = false;
  newNote.value = "";
  errMessage.value = "";
};
</script>

<template>
  <main>
    <div v-if="showModal" class="overlay">
      <div class="modal">
        <textarea
          v-model.trim="newNote"
          name="note"
          id="note"
          cols="30"
          rows="10"
        ></textarea>
        <p class="errMsg" v-if="errMessage">{{ errMessage }}</p>
        <button @click="addNote">Add Note</button>
        <button @click="showModal = false" class="close">Close</button>
      </div>
    </div>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button @click="showModal = true">
          <Icon icon="ic:outline-plus" width="25" />
        </button>
      </header>
      <div class="cards-container">
        <div
          v-for="note in notes"
          :key="note.id"
          class="card"
          :style="{ backgroundColor: note.backgroundColor }"
        >
          <p class="main-text">{{ note.text }}</p>
          <p class="date">{{ note.date }}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
main {
  height: 100vh;
  width: 100vw;
  background-color: #dfe4ea;

  .overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.77);
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: center;
    .modal {
      display: flex;
      flex-direction: column;
      width: 450px;
      padding: 30px;
      position: relative;
      border-radius: 15px;
      background-color: #fff;
      textarea {
        outline: none;
        border: 3px solid black;
        padding: 10px;
      }
      .errMsg {
        color: #ff6b81;
      }
      button {
        padding: 10px 20px;
        margin-top: 15px;
        font-size: 20px;
        width: 100%;
        background-color: #0a3d62;
        color: #fff;
        cursor: pointer;
        border: none;
      }
      .close {
        background-color: #ff6b81;
      }
    }
  }

  .container {
    max-width: 1000px;
    padding: 10px;
    margin: 0 auto;

    header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 20px;

      h1 {
        color: #0a3d62;
        font-size: 75px;
        font-weight: bold;
        font-family: Arial, Helvetica, sans-serif;
      }
      button {
        width: 50px;
        height: 50px;
        border-radius: 100%;
        border: none;
        font-size: 30px;
        background-color: #0a3d62;
        color: #fff;
        cursor: pointer;
      }
    }
    .cards-container {
      display: flex;
      flex-wrap: wrap;
      .card {
        width: 225px;
        height: 225px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        background-color: #0a3d62;
        border-radius: 15px;
        margin-right: 20px;
        margin-bottom: 20px;
        padding: 10px;
        p {
          color: #fff;
          font-size: 12px;
        }
      }
    }
  }
}
</style>
