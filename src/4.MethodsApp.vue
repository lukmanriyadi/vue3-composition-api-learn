<template>
<div>count : {{ counter }} from ref</div>
<div>count : {{ counter2.value }} from reactive</div>
<button @click="add">add</button>
</template>

<script>
import { ref, reactive } from 'vue';
export default {
  setup() {
    const counter = ref(0);
    const counter2 = reactive({
      value: 0,
    });
    const add = () => {
      counter.value++;
      counter2.value++;
    }
    return {
      counter,counter2,
      add,
    }
  }
}
</script>

<style>

</style>