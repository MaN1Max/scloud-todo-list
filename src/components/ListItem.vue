<script setup>
const props = defineProps({
  task: Object
});
</script>

<template>
  <div class="d-flex flex-row task-n-status-list-text-n-button-block">
    <div class="task-n-status-list-text">{{ props.task.name }}</div>
    <div class="d-flex task-n-status-list-button-wrapper">
      <button class="task-n-status-list-button">
        {{ props.task.status }}
      </button>
    </div>
  </div>
  <div class="task-n-status-list-separator"></div>
</template>
