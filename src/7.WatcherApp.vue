<template>
<div>count : {{ counter }} </div>
<button @click="add">add</button>
</template>

<script>
import { ref, reactive, computed, watchEffect, watch } from 'vue';
export default {
  setup() {
    const counter = ref(0);
    const foo = reactive({
      bar: 1,
    });
    const add = () => {
      counter.value++;
    }
    // watch(counter, (newVal, oldVal) => {
    //   console.log(newVal, oldVal);
    // });
    // watch(() => counter.value, (newVal, oldVal) => {
    //   console.log(newVal, oldVal);
    // });
    watch([counter, foo], (newVal, oldVal) => {
      console.log(newVal, oldVal);
    });

    return {
      counter,
      add,
    }
  }
}
</script>

<style>

</style>