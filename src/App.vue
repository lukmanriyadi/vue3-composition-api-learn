<template>
    <div class="container">
        <div class="card">
            <div class="card-body">
                <h5 class="card-title">SIMPLE TODO APP</h5>
                <div class="row">
                    <div class="col-10">
                        <input @keyup.enter="sumbitTodo" v-model="todo" type="text" class="form-control" placeholder="Add new todo" />
                    </div>
                    <div class="col-2">
                        <button @click="sumbitTodo" class="btn btn-primary">Add</button>
                    </div>
                </div>
               <ListComponent 
               :todos="todos"
               @removeTodo="removeTodo"
               @toggleTodo="toggleTodo" 
               />
               <small>Count todo now is : {{ countTodos }}</small>
            </div>
        </div>
    </div>
</template>

<script>
import { ref, reactive, computed, onMounted } from "vue";
import ListComponent from "./components/ListComponent.vue";
export default {
    components: {
        ListComponent,
    },
    setup() {
        const todo = ref("");
        const todos = reactive([
        ]);
        onMounted(() => {
            const localTodos = localStorage.getItem("todos");
            if (localTodos) {
                todos.push(...JSON.parse(localTodos));
            }
        });
        const sumbitTodo = () => {
            const newTodo = {
                title: todo.value,
                done: false,
            };
            todos.push(newTodo);
            todo.value = "";
            saveToLocalStorages();
        };
        const removeTodo = (index) => {
            todos.splice(index, 1);
            saveToLocalStorages();
        };
        const toggleTodo = (index) => {
            todos[index].done = !todos[index].done;
            saveToLocalStorages();
        };
        const countTodos = computed(() => {
            return todos.length;
        });
        const saveToLocalStorages = () => {
            localStorage.setItem("todos", JSON.stringify(todos));
        };

        return {
            todo,
            todos,
            countTodos,
            sumbitTodo,
            removeTodo,
            toggleTodo,
            saveToLocalStorages,
        };
    }
};
</script>

<style></style>
