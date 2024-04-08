<script setup>
defineProps(['selfRemove', 'todoElem','onClickProp'])
</script>
<template>
    <div class="shadow my-3 rounded row todo">
            <input class="col-sm-1" type="checkbox" :disabled=isEdit> 
            <input class="col-sm" type="text" name="noteText" v-model="todoText" :readonly="!isEdit"
                v-on:change="$props.todoElem.text = this.todoText" @click="methods.click"/>
            <button class="col-sm-1 bi-pencil btn btn-warning" @click="isEdit = !isEdit" :hidden=isEdit></button>
            <button class="col-sm-1 bi-check-lg btn btn-success" @click="isEdit = !isEdit" :hidden=!isEdit></button>
            <button class="col-sm-1 bi-slash-circle btn btn-danger" :disabled=isEdit
                @click="selfRemove($props.todoElem)"></button>
    </div>
</template>
<script>
export default {
    data() {
        return {
            isEdit: false,
            todoText: this.$props.todoElem.text,
            methods : {
                click: () => {
                    document.getElementsByClassName("todo")[0].classList.add("todo-glow")
                    this.$props.onClickProp(this.$props.todoElem);
                }
            }
        }
    }
}
</script>