<script setup>
const props = defineProps({
  tasks: Array
})

const getTaskCount = (status) => {
  return props.tasks.reduce((total, task) => {
    if(task.status === status)
      total++
    return total;
  }, 0)
}
</script>

<template>
  <div class="d-flex flex-column current-task-block">
    <div class="current-task-n-add-task-text">
      Текущие задачи
    </div>
    <div class="d-flex flex-row open-in-progress-closed-task-block">
      <div class="d-flex flex-row open-in-progress-closed-task-item">
        <img class="open-in-progress-closed-task-item-img" src="/blue-info.svg" alt="info_icon">
        <div class="open-in-progress-closed-task-item-text">Открыто - {{ getTaskCount("Открыт") }}</div>
      </div>
      <div class="d-flex flex-row open-in-progress-closed-task-item">
        <img class="open-in-progress-closed-task-item-img" src="/orange-info.svg" alt="info_icon">
        <div class="open-in-progress-closed-task-item-text">В работе - {{ getTaskCount("В работе") }}</div>
      </div>
      <div class="d-flex flex-row open-in-progress-closed-task-item">
        <img class="open-in-progress-closed-task-item-img" src="/green-info.svg" alt="info_icon">
        <div class="open-in-progress-closed-task-item-text">Закрыто - {{ getTaskCount("Закрыт") }}</div>
      </div>
    </div>
  </div>
</template>
