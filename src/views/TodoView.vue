<template>
    <div>
        <h2>Список задач</h2>
        <form @submit.prevent="addTodo" class="mb-4">
            <div class="input-group">
                <input v-model="newTodo" type="text" class="form-control" placeholder="Введите новую задачу" required />
                <button type="submit" class="btn btn-primary">Добавить</button>
            </div>
        </form>
        <ul class="list-group">
            <li v-for="(todo, index) in todos" :key="index"
                class="list-group-item d-flex justify-content-between align-items-center">
                {{ todo }}
                <button class="btn btn-danger btn-sm" @click="removeTodo(index)">Удалить</button>
            </li>
        </ul>
        <p v-if="!todos.length" class="text-muted mt-3">Пока нет задач. Добавьте одну выше!</p>
    </div>
</template>

<script setup>
import { ref } from 'vue'

// Реактивные данные с Composition API
const newTodo = ref('')
const todos = ref([])

// Методы
const addTodo = () => {
    if (newTodo.value.trim()) {
        todos.value.push(newTodo.value)
        newTodo.value = ''
    }
}

const removeTodo = (index) => {
    todos.value.splice(index, 1)
}
</script>