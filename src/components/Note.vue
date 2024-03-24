<script setup>
    import DeleteModal from './DeleteModal.vue';
    const props = defineProps(['selfRemove', "index"])
</script>
<template>
    <div class="card shadow rounded my-3">
        <div class="row">
            <div class="col-sm-2"><input type="checkbox" :disabled=isEdit></div>
            <div class="col-8"><input type="text" name="noteText" v-model="noteText" :disabled=!isEdit
                    ></div>
            <div class="col-sm-1">
                <button class="btn btn-warning bi bi-pencil" @click="isEdit = !isEdit" :hidden=isEdit></button>
                <button class="btn btn-success bi bi-check-lg" @click="isEdit = !isEdit" :hidden=!isEdit></button>
            </div>
            <div class="col-sm-1"><button class="btn btn-danger bi bi-slash-circle" :disabled=isEdit
                    @click="selfRemove($props.index)"></button></div>
            <DeleteModal :elemName="'заметку'" :closeModal="methods.closeModal"></DeleteModal>
        </div>
    </div>

</template>
<script>
export default {
    data() {
        return {
            isEdit: false,
            modal: null,
            noteText: 'Новое дело ' + this.$props.index,
            methods: {
                askToDelete: () => {
                    this.modal = new bootstrap.Modal('#delete_modal')
                    console.log(this.modal)
                    this.modal.elemTitle = this.noteText
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