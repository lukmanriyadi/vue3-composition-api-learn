<template>
<div>count : {{ counter }} from ref</div>
<div>count : {{ counter2.value }} from reactive</div>
<button @click="add">add</button>
<div>result : {{ result }}</div>
</template>

<script>
import { ref, reactive, computed } from 'vue';
export default {
  setup() {
    const counter = ref(0);
    const counter2 = reactive({
      value: 0,
    });
    const addNum = ref(1);
    const add = () => {
      counter.value++;
      counter2.value++;
    }
    const result = computed(() => {
      return counter.value + addNum.value;
    })
    return {
      counter,counter2,
      add,
      result,
    }
  }
}
</script>

<style>

</style>