<script setup>
import Notes from '../components/Notes.vue'
import TodoList from '../components/TodoList.vue'
</script>
<template>
    <main class="container">
        <div class="row">
            <TodoList class="col-sm-5"></TodoList>
            <div class="col-sm-2 vr .d-none .d-sm-block"></div>
            <Notes class="col-sm-5"></Notes>
        </div>
    </main>
</template>
<script>
// Здесь исходный код компонента
</script>