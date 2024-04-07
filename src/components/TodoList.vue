<script setup>
import TodoElement from './TodoElement.vue'
</script>
<template>
    <!--Здесь представление компонента (код на HTML)-->
    <main>
        <h2>Мой список дел</h2>
        <div v-for="todo in todos" :key="todo">
                <TodoElement :selfRemove="methods.removeTodo" :todoElem="todo"/>
        </div>

        <button class="btn btn-primary" @click="methods.addTodo()">Добавить задачу</button>
    </main>

</template>
<script>
export default {
    data() {
        return {
            todos: [],
            methods: {
                addTodo: () => {
                    this.todos.push({
                        toRemove: false,
                        todoText: "Новое дело"
                    });
                },
                removeTodo: (elem) => {
                    elem.toRemove = true
                    this.methods.updateTodos()
                },
                updateTodos: () => {
                    this.todos = this.todos.filter((el) => {
                        return !el.toRemove
                    })
                },
            }
        }
    }
}
</script>