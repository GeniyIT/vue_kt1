<template>
    <div>
        <TodoItem
            v-for="todo in todos"
            :key="todo.id"
            :id="todo.id"
            :title="todo.title"
            :completed="todo.completed"
            @removeTodo="removeTodo"
            @changeTodo="changeTodo"
        />
    </div>
</template>

<script setup>
import TodoItem from './TodoItem.vue';
import { defineProps, defineEmits } from 'vue';

const props = defineProps(['todos']);

const removeTodo = (id) => {
    emits('removeTodo', id);
};

const changeTodo = (id) => {
    emits('changeTodo', id);
};

const emits = defineEmits(['removeTodo', 'changeTodo']);
</script>

