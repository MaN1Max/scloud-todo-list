<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  isOpen: Boolean,
  closeModal: Function,
  modalCurrentTask: Object,
  modalCurrentKey: Number,
  deleteTask: Function,
  statusChange: Function,
  submitChanges: Function,
  taskNameChange: Function,
  modalCurrentName: String,
  modalActiveStatus: String
});
</script>

<template>
  <div v-if="props.isOpen" class="d-flex modal-bg">
    <div class="d-flex flex-column modal-block">
      <div class="d-flex modal-header">
        Изменение задачи
        <button class="d-flex close-modal-button" @click="props.closeModal">
          <img class="close-modal-button-img" src="/close-modal-icon.svg" alt="close-modal-icon">
        </button>
      </div>
      <div class="d-flex flex-column modal-body">
        <input class="modal-input" type="text" placeholder="Текст" @change="props.taskNameChange" :value="props.modalCurrentName || props.modalCurrentTask.name">
        <div class="modal-separator"></div>
        <div class="d-flex modal-status-buttons-block">
          <button :class="props.modalActiveStatus === 'Открыт' ? 'modal-status-button active' : 'modal-status-button'" @click="props.statusChange('Открыт')">
            Отложить
          </button>
          <button :class="props.modalActiveStatus === 'В работе' ? 'modal-status-button active' : 'modal-status-button'" @click="props.statusChange('В работе')">
            В работу
          </button>
          <button :class="props.modalActiveStatus === 'Закрыт' ? 'modal-status-button active' : 'modal-status-button'" @click="props.statusChange('Закрыт')">
            Закрыть
          </button>
        </div>
        <div class="d-flex modal-save-n-delete-task-block">
          <button class="d-flex modal-save-task-button" @click="props.submitChanges">
            Применить
          </button>
          <button class="d-flex modal-delete-task-button" @click="props.deleteTask">
            Удалить задачу
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
