<script setup>
const props = defineProps({
  tasks: Array
})

const getTaskCount = (status) => {
  return props.tasks.reduce((total, task) => {
    if (task.status === status)
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
        <img alt="info_icon" class="open-in-progress-closed-task-item-img" src="/blue-info.svg">
        <div class="open-in-progress-closed-task-item-text">Открыто - {{ getTaskCount("Открыт") }}</div>
      </div>
      <div class="d-flex flex-row open-in-progress-closed-task-item">
        <img alt="info_icon" class="open-in-progress-closed-task-item-img" src="/orange-info.svg">
        <div class="open-in-progress-closed-task-item-text">В работе - {{ getTaskCount("В работе") }}</div>
      </div>
      <div class="d-flex flex-row open-in-progress-closed-task-item">
        <img alt="info_icon" class="open-in-progress-closed-task-item-img" src="/green-info.svg">
        <div class="open-in-progress-closed-task-item-text">Закрыто - {{ getTaskCount("Закрыт") }}</div>
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

.current-task-block {
  box-sizing: border-box;
  width: 100%;
  padding: 40px 24px 40px 24px;
  border-radius: 48px;
  background-color: #FFFFFF;
}

.current-task-n-add-task-text {
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 700;
  font-size: 24px;
  line-height: 32px;
  text-align: left;
  color: #333333;
}

.open-in-progress-closed-task-block {
  flex-wrap: wrap;
  flex-direction: column;
  justify-content: space-between;
  gap: 12px;
  margin-top: 24px;
}

.open-in-progress-closed-task-item {
  box-sizing: border-box;
  justify-content: center;
  align-items: center;
  min-width: 161px;
  height: 48px;
  padding: 12px 24px 12px 24px;
  border-radius: 50px;
  border: 1px solid #EAEAEA
}

.open-in-progress-closed-task-item-img {
  width: 20px;
  height: 20px;
  margin-right: 8px;
}

.open-in-progress-closed-task-item-text {
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 700;
  font-size: 14px;
  line-height: 24px;
  text-align: center;
  color: #333333;
}

@media screen and (min-width: 1222px) {
  .current-task-block {
    width: calc(50% - 12px);
  }
}

@media screen and (min-width: 660px) {
  .open-in-progress-closed-task-block {
    flex-wrap: wrap;
    flex-direction: row;
    justify-content: space-between;
    gap: 0;
  }
}
</style>
