<template>
  <div class="mt-4">
    <ul class="list-option">
      <li v-for="todo, index in todos" :key="todo" class="list-option-item">
        <div class="row">
          <div class="col">
            <span :class="todo.done ? 'done' : ''">{{ todo.title }}</span>
          </div>
          <div class="col-auto">
            <div class="row gx-2">
              <div class="col">
                <button @click="toggleTodo(index)" class="btn btn-sm btn-warning">Done</button>
              </div>
              <div class="col">
                <button @click="removeTodo(index)" class="btn btn-sm btn-danger">X</button>
              </div>
            </div>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref, reactive } from "vue";
export default {
    emits: ["removeTodo", "toggleTodo"],
    props: {
        todos: {
            type: Array,
            required: true,
            default: () => [],
        }
    },
    setup(props, { emit }) {
        const removeTodo = (index) => {
            emit("removeTodo", index);
        };
        const toggleTodo = (index) => {
            emit("toggleTodo", index);
        };
        return {
            removeTodo,
            toggleTodo,
        };
    }
};
</script>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>
