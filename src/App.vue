<script setup>
import { ref } from "vue";
const count = ref(0);

const increment = () => {
  count.value = count.value + 1;
};
const decrement = () => {
  count.value = count.value - 1;
};
</script>

<template>
  <main>
    <div>
      <h4>This current counter is..</h4>
      <h1>{{ count }}</h1>
      <button @click="decrement">-</button>
      <button @click="increment">+</button>
    </div>
  </main>
</template>

<style lang="scss" scoped>
main {
  background-color: aliceblue;
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  div {
    text-align: center;
    h4 {
      font-size: 2rem;
    }
    h1 {
      font-size: 3rem;
    }

    button {
      padding: 1px 25px;
      margin: 5px;
      font-size: 40px;
    }
  }
}
</style>
