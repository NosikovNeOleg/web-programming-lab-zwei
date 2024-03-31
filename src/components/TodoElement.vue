<script setup>
defineProps(['selfRemove', 'todoElem'])
</script>
<template>
    <div class="card shadow rounded my-3">
        <div class="row">
            <div class="col-sm-2"><input type="checkbox" :disabled=isEdit></div>
            <div class="col-8"><input type="text" name="noteText" v-model="todoText" :disabled=!isEdit
                    v-on:change="$props.todoElem.todoText = this.todoText"></div>
            <div class="col-sm-1">
                <button class="btn btn-warning bi bi-pencil" @click="isEdit = !isEdit" :hidden=isEdit></button>
                <button class="btn btn-success bi bi-check-lg" @click="isEdit = !isEdit" :hidden=!isEdit></button>
            </div>
            <div class="col-sm-1"><button class="btn btn-danger bi bi-slash-circle" :disabled=isEdit
                    @click="selfRemove($props.todoElem)"></button></div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            isEdit: false,
            todoText: this.$props.todoElem.todoText,
                
        }
    }
}
</script>