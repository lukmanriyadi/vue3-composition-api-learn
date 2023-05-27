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
    watchEffect(() => {
      console.log(counter.value);
    },{
      // flush: 'pre',
      flush: 'post',
      onTrack: (event) => {
        console.log(event);
      },
      // onTrigger: (event) => {
      //   console.log(event);
      // }
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