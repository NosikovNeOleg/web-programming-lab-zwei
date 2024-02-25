<script setup>
import Note from './Note.vue'
</script>
<template>
<!--Здесь представление компонента (код на HTML)-->
<main>
    <h2>Мои заметки</h2>
    <ul id="notesList">
        <li v-for="note,index in notes">
          <component :is="Note" />
		</li>
    </ul>
    
    <button class="btn btn-primary" @click="methods.addNote()">Добавить заметку</button>
</main>
</template>
<script>
export default {
  data() {
    return {
        newItem : Note,
        notes: [],
        methods: {
            addNote: () =>  {
		        this.notes.push(this.newItem);
	        }
        }
    }
    }
}
</script>