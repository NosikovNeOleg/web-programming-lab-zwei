<script setup>
import Note from './Note.vue'
</script>
<template>
  <main>
    <h2>Мои заметки</h2>
    <ul id="notesList">
      <li v-for="note,index in notes">
        <note :index="index" :selfRemove="methods.removeNote"/>
      </li>
    </ul>

    <button class="btn btn-primary" @click="methods.addNote()">Добавить заметку</button>
  </main>
</template>
<script>
export default {
  data() {
    return {
      newItem: null,
      notes: [],
      methods: {
        addNote: () => {
            this.newItem = Note
            this.notes.push(this.newItem);
        },
        removeNote: (index) => {
          console.log(index)
          this.notes.splice(index,1)
        }
      }
    }
  }
}
</script>