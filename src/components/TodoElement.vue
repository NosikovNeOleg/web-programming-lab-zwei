<script setup>
defineProps(['selfRemove', 'todoElem'])
</script>
<template>
    <div class="row shadow rounded my-3">
            <input class="col-sm-1" type="checkbox" :disabled=isEdit>
            <textarea class="col-sm" rows="1" name="noteText" v-model="todoText" :disabled=!isEdit
                v-on:change="$props.todoElem.todoText = this.todoText"></textarea>
            <button class="col-sm-1 btn btn-warning bi-pencil" @click="isEdit = !isEdit" :hidden=isEdit></button>
            <button class="col-sm-1 btn btn-success bi-check-lg" @click="isEdit = !isEdit" :hidden=!isEdit></button>
            <button class="col-sm-1 btn btn-danger bi-slash-circle" :disabled=isEdit
                @click="selfRemove($props.todoElem)"></button>
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