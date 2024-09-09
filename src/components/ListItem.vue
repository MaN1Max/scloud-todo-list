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
