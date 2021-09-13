<template>
  <div v-show="show" class="modal" @click="closeModal">
    <div class="dialog__content">
      <h2 class="dialog__title" v-text="title"></h2>
      <p class="dialog__description" v-text="description"></p>
    </div>
    <div class="dialog__footer">
      <button @click="cancel" class="dialog__cancel">Cancel</button>
      <button @click="confirm" class="dialog__confirm">Confirm</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['show', 'title', 'description', 'cancel', 'confirm', 'index'],
  methods: {
    closeModal() {
      this.$emit('close')
    }
  }
}
</script>

<style>
  .modal{
    position: relative;
    width: 400px;    
    padding: 20px;
    margin: 100px auto;
    background: rgb(207, 205, 205);
    border-radius: 10px;

    text-align: center;
  }
.dialog__footer {
   display: block;
   text-align: right;  
} 
 .dialog__footer button{
   margin-left: 5px;
} 
</style>