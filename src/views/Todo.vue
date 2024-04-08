<script setup>
import Notes from '../components/Notes.vue'
import TodoList from '../components/TodoList.vue'
</script>
<template>
    <main class="container">
        <div class="row">
            <TodoList :selectTodo="methods.selectTodo" :selectedTodo="selectedTodo" class="col-sm-5"></TodoList>
            <div class=".d-sm-block col-sm-2 .d-none vr"></div>
            <Notes :selectedTodo="selectedTodo" :notes="methods.getNotes(selectedTodo)" class="col-sm-5"></Notes>
        </div>
    </main>
</template>
<script>
export default {
    data() {
        return {
            selectedTodo: null,
            methods: {
                selectTodo: (todo) => {
                    if (this.selectedTodo === todo) {
                        this.selectedTodo = null
                    } else {
                        console.log(todo)
                        this.selectedTodo = todo;
                    }
            },
                getNotes: (todo) => {
                    if (todo){
                        return todo.notes;
                    } else {
                        return [];
                    }
                }
        }
        }
    }
}
</script>