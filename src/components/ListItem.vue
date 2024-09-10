<script setup>
const props = defineProps({
  task: Object,
  currentKey: Number,
  openModal: Function
});
</script>

<template>
  <div class="d-flex flex-row task-n-status-list-text-n-button-block">
    <div class="task-n-status-list-text">{{ props.task.name }}</div>
    <div class="d-flex task-n-status-list-button-wrapper">
      <button class="task-n-status-list-button" @click="openModal(props.task, props.currentKey)">
        {{ props.task.status }}
      </button>
    </div>
  </div>
  <div class="task-n-status-list-separator"></div>
</template>

<style scoped>
.d-flex {
  display: flex;
}
.task-n-status-list-text-n-button-block {
  margin-top: 8px;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}
.task-n-status-list-text {
  width: 90%;
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  color: #333333;
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
}
.task-n-status-list-button-wrapper {
  width: 102px;
}
.task-n-status-list-button {
  margin: auto;
  height: 28px;
  padding: 5px 16px 5px 16px;
  border-radius: 39px;
  background-color: #F4F4F4;
  cursor: pointer;
  border: none;
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 400;
  font-size: 12px;
  line-height: 20px;
  color: #333333;
}
.task-n-status-list-separator {
  width: 100%;
  margin-top: 8px;
  border-bottom: 1px solid #EAEAEA;
}
</style>
