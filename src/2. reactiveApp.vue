<template>
  <pre>{{ user }}</pre>
  <pre>{{ user2 }}</pre>
  <h1>{{ title }}</h1>
  <h2>{{ title2 }}</h2>
</template>

<script>
import { ref, reactive } from 'vue';
export default {
  setup() {
    const user = ref({ name: 'vben', age: 20 });
    const user2 = reactive({ name: 'vben2', age: 20 });
    const title = ref('hello');
    const title2 = reactive('hello');
    setTimeout(() => {
      title.value = 'world';
      title2= 'world';
      user.value.age = 21; //not reactive
      user2.age = 21; //reactive
    }, 2000);
    return {
      user,user2,
      title,title2
    }
  }
}
</script>

<style>

</style>