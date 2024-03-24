<script setup>
import TodoElement from './TodoElement.vue'
</script>
<template>
    <!--Здесь представление компонента (код на HTML)-->
    <main>
        <h2>Мой список дел</h2>
        <ul id="todoList">
            <li v-for="todo, index in todos">
                <component :is="TodoElement" />
            </li>
        </ul>

        <button class="btn btn-primary" @click="methods.addTodo()">Добавить задачу</button>
    </main>

</template>
<script>
export default {
    data() {
        return {
            newItem: TodoElement,
            todos: [],
            methods: {
                addTodo: () => {
                    this.todos.push(this.newItem);
                }
            }
        }
    }
}
</script>