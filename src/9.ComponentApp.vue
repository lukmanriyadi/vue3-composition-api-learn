<template>
  <UserComponent 
  :label="label" 
  :user="user" 
  class="active" 
  blablabla="testing"
  @submit="submit"
  >
    <div>Ini Slot</div>
  </UserComponent>
  <button @click="changeName">Change </button>
</template>

<script>
import { ref, reactive } from "vue";
import UserComponent from "./components/UserComponent.vue";

export default {
    setup() {
        const user = reactive({
            name: "John Doe",
            email: ""
        });
        const label = ref("User Details");
        const changeName = () => {
            user.name = "Jane Doe";
        };

        const submit = (data) => {
            console.log(data);
        };
        return {
            user,
            label,
            changeName,
            submit
        };
    },
    components: { UserComponent }
};
</script>

<style></style>
