<script setup>
import Note from './Note.vue'
import DeleteModal from './DeleteModal.vue';
</script>
<template>
  <main>
    <h2>Мои заметки</h2>
    <ul v-for="note, index in notes" :key="note">
      <Note :noteElem=note :text=note.text :selfRemove="methods.askToDelete"></Note>
    </ul>

    <button class="btn btn-primary" @click="methods.addNote()">Добавить заметку</button>
    <DeleteModal :elemName="'заметку'" :elem="tempElem" :closeModal="methods.closeModal" :deleteFromModal="methods.removeNote"></DeleteModal>

  </main>
</template>
<script>
export default {
  data() {
    return {
      notes: [],
      int: 0,
      modal: null,
      tempElem: {},
      methods: {
        addNote: () => {
          this.notes.push((
            {
              toRemove: false,
              noteText: "Новая заметка"
            }
          ))
        },

        removeNote: (elem) => {
          elem.toRemove = true
          this.modal.hide();
          this.methods.updateNotes()
        },
        updateNotes: () => {
          this.notes = this.notes.filter((el) => {
            return !el.toRemove
          })
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