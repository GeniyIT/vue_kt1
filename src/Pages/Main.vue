<template>
    <div>
        <AddTodo @addNewTodo="addNewTodo" />
        <TodoList :todos="todos" @removeTodo="removeTodo" @changeTodo="changeTodo" />
    </div>
</template>

<script setup>
import { ref } from 'vue';
import TodoList from '../components/TodoList.vue';
import AddTodo from '../components/AddTodo.vue';

const todos = ref([
    { id: 1, title: 'Позавтракать', completed: true },
    { id: 2, title: 'Почистить огурцы', completed: false },
    { id: 3, title: 'Помыть кота', completed: true }
]);

const removeTodo = id => {
    todos.value = todos.value.filter(elem => elem.id !== id);
};

const changeTodo = id => {
    todos.value = todos.value.map(elem => {
        if (elem.id === id) {
            elem.completed = !elem.completed;
        }
        return elem;
    });
};

const addNewTodo = title => {
    todos.value.push({
        id: Date.now(),
        title,
        completed: false
    });
};
</script>
