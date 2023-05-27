<template>
  <h1>{{ msg }}</h1>
</template>

<script>
import { ref } from 'vue';
export default {
  setup() {
    const msg = ref('Hello Vue 3 + Vite');
    setTimeout(() => {
      msg.value = 'Hello Vue 3 + Vite + TypeScript + ESLint + Prettier';
    }, 2000);
    return {
      msg
    }
  }
}
</script>

<style>

</style>