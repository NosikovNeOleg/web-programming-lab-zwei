<script setup>
import Notes from '../components/Notes.vue'
import TodoList from '../components/TodoList.vue'
</script>
<template>
    <main class="container">
        <div class="row">
            <TodoList class="col-5"></TodoList>
            <Notes class="col-5"></Notes>
        </div>
    </main>
    <footer class="footer">Основные действия со списком заметок:
        ● удаление заметки (необходимо подтверждение).
        4. На главной странице должна быть область для изменения заметки,
        которая позволяет отредактировать определенную заметку, отметить
        пункты списка дел.
        Действия с пунктами списка дел:
        ● добавить.
        ● удалить.
        ● отредактировать текст.
        ● отметить как выполненный</footer>
</template>
<script>
// Здесь исходный код компонента
</script>