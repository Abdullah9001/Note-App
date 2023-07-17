<script setup>
import { Icon } from "@iconify/vue";
import { ref } from "vue";

const showModal = ref(false);
const newNote = ref("");
</script>

<template>
  <main>
    <div v-show="showModal" class="overlay">
      <div class="modal">
        <textarea
          v-model="newNote"
          name="note"
          id="note"
          cols="30"
          rows="10"
        ></textarea>
        <button>Add Note</button>
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
        <div class="card">
          <p class="main-text">this is my new note</p>
          <p class="date">the date</p>
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
      width: 400px;
      padding: 30px;
      position: relative;
      border-radius: 15px;
      background-color: #fff;
      textarea {
        outline: none;
        border: 3px solid black;
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
