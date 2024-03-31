<script setup>
    defineProps(['selfRemove', 'noteElem'])
</script>
<template>
    <div class="card shadow rounded my-3">
        <div class="row">
            <div class="col-sm-2"><input type="checkbox" :disabled=isEdit></div>
            <div class="col-sm-8"><input type="text" name="noteText" v-model="noteText" :disabled=!isEdit v-on:change="$props.noteElem.noteText = this.noteText"
                    ></div>
            <div class="col-sm-1">
                <button class="btn btn-warning bi bi-pencil" @click="isEdit = !isEdit" :hidden=isEdit></button>
                <button class="btn btn-success bi bi-check-lg" @click="isEdit = !isEdit" :hidden=!isEdit></button>
            </div>
            <div class="col-sm-1"><button class="btn btn-danger bi bi-slash-circle" :disabled=isEdit
                    @click="selfRemove($props.noteElem)"></button></div>
        </div>
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