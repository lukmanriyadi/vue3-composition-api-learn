<template>
    <div>
        <h3>{{ label }}</h3>
        <p>{{ user.name }}</p>
        <p>{{ description }}</p>
        <slot></slot>
        <hr />
        <button @click="submit">Submit</button>
    </div>
</template>

<script>
import { ref, toRefs, computed, onMounted } from "vue";
export default {
    props: {
        label: {
            type: String,
            required: true,
            default : ''
        },
        user: {
            type: Object,
            required: true,
            default : () => ({})
        },
    },
    setup(props, { emit, slots, attrs }) {
        const { label, user } = toRefs(props);
        const description = computed(() => {
            return `${user.value.name} is ${label.value}`;
        });
        
        onMounted(() => {
            console.log(attrs, slots);
        });

        const submit = () => {
            emit("submit", "Hello from UserComponent");
        };
        return {
            description, submit
        };
    },
}
</script>

<style>

</style>