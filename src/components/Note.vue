<script setup>
</script>
<template>
    <div class="card shadow rounded my-3">
    <div class="row">
        <div class="col-sm-2"><input  type="checkbox"></div>
        <div class="col-8"><input type="text"></div>
        <div class="col-sm-1"><button class="btn btn-warning bi bi-pencil" @click="methods.addTodo()"></button></div>
        <div class="col-sm-1"><button class="btn btn-danger bi bi-slash-circle"></button></div>
    </div>
</div>
</template>
<script>
    export default {
      data() {
        return {
            todos: [],
            methods: {
                addTodo: () =>  {
                    this.todos.push(this.newItem);
                }
            }
        }
        }
    }
    </script>