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

<style scoped>
.d-flex {
  display: flex;
}
.flex-column {
  flex-direction: column;
}
.modal-bg {
  position: fixed;
  z-index: 10;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: #EAEAEA80;
  backdrop-filter: blur(4px);
}
.modal-block {
  box-sizing: border-box;
  width: 375px;
  height: 278px;
  margin: auto;
  padding: 24px;
  border-radius: 16px;
  background: #FFFFFF;
}
.modal-header {
  justify-content: space-between;
  align-items: center;
  font-family: 'Montserrat', sans-serif;
  font-weight: 700;
  font-size: 18px;
  line-height: 26px;
  text-align: left;
}
.close-modal-button {
  background: transparent;
  border: none;
  cursor: pointer;
}
.close-modal-button-img {
  width: 24px;
  height: 24px;
  margin: auto;
}
.modal-body {
  margin-top: 24px;
}
.modal-input {
  box-sizing: border-box;
  width: 100%;
  min-height: 52px;
  padding: 16px 73px 16px 16px;
  border-radius: 24px;
  border: 1px solid #F4F4F4;
}
.modal-input::placeholder {
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 400;
  font-size: 14px;
  line-height: 24px;
  color: #333333;
}
.modal-separator {
  width: 100%;
  margin-top: 16px;
  border: 1px solid #EAEAEA;
}
.modal-status-buttons-block {
  margin-top: 16px;
  gap: 8px;
}
.modal-status-button {
  min-height: 28px;
  padding: 5px 16px 5px 16px;
  border-radius: 39px;
  background-color: #F4F4F4;
  cursor: pointer;
  border: 1px solid #F4F4F4;
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 400;
  font-size: 12px;
  line-height: 20px;
  color: #333333;
}
.modal-status-button.active {
  border: 1px solid #FF6600;
}
.modal-save-n-delete-task-block {
  margin-top: 24px;
  justify-content: space-between;
}
.modal-save-task-button {
  width: fit-content;
  align-items: center;
  justify-content: center;
  height: 40px;
  padding: 8px 24px 8px 24px;
  border-radius: 50px;
  background: #FF6600;
  border: none;
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 700;
  font-size: 14px;
  line-height: 24px;
  color: #FFFFFF;
  cursor: pointer;
}
.modal-delete-task-button {
  width: fit-content;
  align-items: center;
  justify-content: center;
  height: 40px;
  padding: 8px 32px 8px 32px;
  border-radius: 50px;
  border: 2px solid #FF6600;
  background: #FFFFFF;
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 700;
  font-size: 14px;
  line-height: 24px;
  color: #FF6600;
  cursor: pointer;
}
</style>
