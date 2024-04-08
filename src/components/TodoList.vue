<script setup>
import TodoElement from './TodoElement.vue'
import DeleteModal from './DeleteModal.vue';
defineProps(['selectTodo','selectedTodo'])
</script>
<template>
    <main>
        <h2>Мой список дел</h2>
        <div v-for="todo in todos" :key="todo"  >
            <TodoElement :onClickProp="selectTodo" :selfRemove="methods.askToDelete" :todoElem="todo"/>
        </div>
        <DeleteModal :elemName="'заметку'" :elem="tempElem" :closeModal="methods.closeModal" :deleteFromModal="methods.removeTodo"></DeleteModal>
        <button class="btn btn-primary" @click="methods.addTodo()">Добавить задачу</button>
    </main>

</template>
<script>
export default {
    data() {
        return {
            todos: [],
            tempElem: {},
            modal: null,
            methods: {
                addTodo: () => {
                    this.todos.push({
                        toRemove: false,
                        text: "Новое дело",
                        notes: []
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
                removeTodo: (elem) => {
                    elem.toRemove = true
                    this.modal.hide();
                    this.methods.updateTodos()
                    if (this.$props.selectedTodo == elem) {
                        this.$props.selectTodo(null);
                    }
                    
                },
                askToDelete: (elem) => {
                    this.tempElem = elem
                    this.modal = new bootstrap.Modal('#delete_modal')
                
                    this.modal.show()
                },
                closeModal: () => {
                    this.modal.hide();
                }
            }
        }
    }
}
</script>