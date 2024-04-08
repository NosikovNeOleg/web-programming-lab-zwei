<script setup>
defineProps(['selfRemove', 'noteElem'])
</script>
<template>
    <div class="shadow my-3 rounded row">
        <input class="col-sm-1" type="checkbox" :disabled=isEdit>
        <input class="col-sm" type="text" name="noteText" v-model="noteText" :disabled=!isEdit
            v-on:change="$props.noteElem.noteText = this.noteText"/>
        <button class="col-sm-1 bi-pencil btn btn-warning" @click="isEdit = !isEdit" :hidden=isEdit></button>
        <button class="col-sm-1 bi-check-lg btn btn-success" @click="isEdit = !isEdit" :hidden=!isEdit></button>
        <button class="col-sm-1 bi-slash-circle btn btn-danger" :disabled=isEdit
            @click="selfRemove(noteElem)"></button>
    </div>
</template>
<script>
export default {
    data() {
        return {
            isEdit: false,
            modal: null,
            noteText: this.$props.noteElem.text,
        }
    }
}
</script>