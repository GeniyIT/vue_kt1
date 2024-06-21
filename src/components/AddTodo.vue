<template>
    <div class="input_elem">
        <input type="text" v-model="newTodo" @keyup.enter="addTodo">
    </div>
</template>

<script setup>
import { ref, defineEmits } from 'vue';

const newTodo = ref('');

const addTodo = () => {
    if (newTodo.value.trim()) {
        emits('addNewTodo', newTodo.value.trim());
        newTodo.value = '';
    }
};

// Define emits explicitly
const emits = defineEmits(['addNewTodo']);
</script>



<style scoped>
.input_elem {
    display: flex;
    justify-content: center;
    margin: 20px 400px;
}

.input_elem > input {
    width: 100%;
    box-shadow: 5px 5px 5px black;
}
</style>
