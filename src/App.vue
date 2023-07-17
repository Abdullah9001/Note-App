<script setup>
import { Icon } from "@iconify/vue";
</script>

<template>
  <main>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button><Icon icon="ic:outline-plus" width="25" /></button>
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

  .container {
    max-width: 1000px;
    padding: 10px;
    margin: 0 auto;

    header {
      display: flex;
      align-items: center;
      justify-content: space-between;

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
