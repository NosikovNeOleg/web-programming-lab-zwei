<script setup>
    const props = defineProps(["elemName", "elem", "closeModal", "deleteFromModal"])
</script>
<template>
    <!-- Modal -->
    <div class="fade modal" id="delete_modal" tabindex="-1" aria-labelledby="delete_modal_label" aria-hidden="true">
                <div class="modal-dialog">
                    <div class="modal-content">
                        <div class="modal-header">
                            <h5 class="modal-title" id="delete_modal_label">Подтвердите удаление </h5>
                            <button type="button" class="btn-close" aria-label="Close" @click="closeModal"></button>
                        </div>
                        <div class="modal-body">
                            Вы действительно хотите удалить {{ elemName }} - {{ elem.text }}?
                        </div>
                        <div class="modal-footer">
                            <button type="button" class="btn btn-secondary" @click="closeModal">Отмена</button>
                            <button type="button" class="btn btn-primary" @click="deleteFromModal(elem)">Удалить</button>
                        </div>
                    </div>
                </div>
            </div>
</template>
<script>
</script>