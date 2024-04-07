<script setup>
    const props = defineProps(["mark","closeModal"])
</script>
<template>
    <!-- Modal -->
    <div class="fade modal" id="thank_modal" tabindex="-1" aria-labelledby="thank_modal_label" aria-hidden="true">
                <div class="modal-dialog">
                    <div class="modal-content">
                        <div class="modal-header">
                            <h5 class="modal-title" id="thank_modal_label">Спасибо за оценку! </h5>
                            <button type="button" class="btn-close" aria-label="Close" @click="closeModal"></button>
                        </div>
                        <div class="modal-body">
                             Ваша оценка - {{ mark }}
                        </div>
                    </div>
                </div>
            </div>
</template>
<script>
</script>