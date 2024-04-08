<script setup>
import Note from './Note.vue'
defineProps(['selectTodo', 'selectedTodo','notes'])
</script>
<template>
  <main>
    <h2>Содержание заметки</h2>
    <div v-for="note in notes" :key="note">
      <Note :noteElem=note :text=note.text :selfRemove="methods.removeNote"></Note>
    </div>
    <div :hidden="selectedTodo !== null" class="quote">Выберите заметку</div>
    <button class="btn btn-primary" @click="methods.addNote()" :hidden="selectedTodo === null">Добавить заметку</button>

  </main>
</template>
<script>
export default {
  data() {
    return {
      int: 0,
      tempElem: {},
      methods: {
        addNote: () => {
          this.$props.selectedTodo.notes.push((
            {
              toRemove: false,
              text: "Новая заметка"
            }
          ))
        },

        removeNote: (elem) => {
          elem.toRemove = true
          this.methods.updateNotes()
        },
        updateNotes: () => {
          this.$props.selectedTodo.notes = this.$props.selectedTodo.notes.filter((el) => {
            return !el.toRemove
          })
        },
        closeModal: () => {
          this.modal.hide();
        }
      }
    }
  }
}
</script>