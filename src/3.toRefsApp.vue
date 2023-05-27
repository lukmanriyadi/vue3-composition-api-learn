<template>
  <h1>{{ name }}</h1>
  <h1>{{ age }}</h1>
</template>

<script>
import { toRefs, reactive } from 'vue';
export default {
  setup() {
    const user = reactive({ name: 'vben2', age: 20 });
    setTimeout(() => {
      user.age = 21; //reactive
    }, 2000);
    return {
      ...toRefs(user),
    }
  }
}
</script>

<style>

</style>