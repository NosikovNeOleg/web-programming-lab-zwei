<script setup>
import ThankModal from '../components/ThankModal.vue';
</script>
<template>
  <div class="container">
    <div class="justify-content-md-center row">
      <label class="text-center col-sm star">
        <input class="invisible" type="radio" id="star1" v-on:input="methods.check">
        <div class="bi-star" id="starImg1"></div>
      </label>
      <label class="text-center col-sm star">
        <input class="invisible" type="radio" id="star2"  v-on:input="methods.check">
        <div class="bi-star" id="starImg2"></div>
      </label>
      <label class="text-center col-sm star">
        <input  class="invisible"type="radio" id="star3"  v-on:input="methods.check">
        <div class="bi-star" id="starImg3"></div>
      </label>
      <label class="text-center col-sm star">
        <input  class="invisible"type="radio" id="star4" v-on:input="methods.check">
        <div class="bi-star" id="starImg4"></div>
      </label>
      <label class="text-center col-sm star">
        <input class="invisible" type="radio" id="star5" v-on:input="methods.check">
        <div class="bi-star" id="starImg5"></div>
      </label>
    </div>
  </div>
  <ThankModal :mark="mark" :closeModal="methods.closeModal"></ThankModal>
  

</template>

<script>
  export default {
    data() {
        return {
          modal: null,
          mark: null,
            methods : {
              check: (smth) => {
                var str = "starImg"
                this.mark = smth.target.id[4];
                for (var iter = 1 ; iter <= 5 ; iter++) {
                  var star = document.getElementById(str + iter);
                  if (iter <= this.mark) {
                    star.classList.remove("bi-star")
                    star.classList.add("bi-star-fill")
                  } else {
                    star.classList.add("bi-star")
                    star.classList.remove("bi-star-fill")
                  }
                } 
                setTimeout(() => {
                  this.modal = new bootstrap.Modal('#thank_modal')
                  this.modal.show()
                  }, 300);
              },
              closeModal: () => {
                this.modal.hide();
              }
            }
        }
    }
}
</script>