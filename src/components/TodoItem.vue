<template>
    <div
        class="todo_item"
        @dblclick="handleRemove"
        @click="handleChange"
        :style="{ backgroundColor: completed ? 'green' : 'red' }"
    >
        <h1>{{ title }}</h1>
    </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps(['id', 'title', 'completed']);

const handleRemove = () => {
    emits('removeTodo', props.id);
};

const handleChange = () => {
    emits('changeTodo', props.id);
};

const emits = defineEmits(['removeTodo', 'changeTodo']);
</script>


<style scoped>
.todo_item {
    display: flex;
    flex-direction: column;
    margin: 20px 170px;
    padding: 10px;
    outline: 2px solid black;
    box-shadow: 5px 5px 5px black;
}
</style>
