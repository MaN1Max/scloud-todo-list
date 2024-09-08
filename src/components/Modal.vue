<script setup>
import { defineProps } from 'vue';

const { isOpen } = defineProps({
  isOpen: Boolean,
});
</script>

<template>
  <div v-if="isOpen" class="modal-mask">
    <div class="modal-wrapper">
      <div ref="target" class="modal-container">
        <div class="modal-header">
          <slot name="header"> default header</slot>
        </div>
        <div class="modal-body">
          <slot name="content"> default content</slot>
        </div>
        <div class="modal-footer">
          <slot name="footer"> default footer</slot>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

.modal-wrapper {
  display: flex;
}

.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}

.modal-container {
  width: fit-content;
  margin: 30vh auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 16px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
}
</style>