<script setup>
defineProps(['selfRemove', 'noteElem'])
</script>
<template>
    <div class="row shadow rounded my-3">
        <input class="col-sm-1" type="checkbox" :disabled=isEdit>
        <textarea class="col-sm"  rows="1" type="text" name="noteText" v-model="noteText" :disabled=!isEdit
            v-on:change="$props.noteElem.noteText = this.noteText"></textarea>
        <button class="col-sm-1 btn btn-warning bi-pencil" @click="isEdit = !isEdit" :hidden=isEdit></button>
        <button class="col-sm-1 btn btn-success bi-check-lg" @click="isEdit = !isEdit" :hidden=!isEdit></button>
        <button class="col-sm-1 btn btn-danger bi-slash-circle" :disabled=isEdit
            @click="selfRemove($props.noteElem)"></button>
    </div>
</template>
<script>
export default {
    data() {
        return {
            isEdit: false,
            modal: null,
            noteText: this.$props.noteElem.noteText
        }
    }
}
</script>