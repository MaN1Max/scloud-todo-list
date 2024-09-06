<script setup>
</script>

<template>
  <div class="d-flex upper-bg-frame">
    <div class="d-flex flex-column content-container border">
      <h1 class="header-text">ToDo List Scloud</h1>
      <div class="d-flex flex-row current-task-n-add-task-block">
        <div class="d-flex flex-column current-task-block">
          <div class="current-task-n-add-task-text">
            Текущие задачи
          </div>
          <div class="d-flex flex-row open-in-progress-closed-task-block">
            <div class="d-flex flex-row open-in-progress-closed-task-item">
              <img class="open-in-progress-closed-task-item-img" src="/blue-info.svg" alt="info_icon">
              <div class="open-in-progress-closed-task-item-text">Открыто - x</div>
            </div>
            <div class="d-flex flex-row open-in-progress-closed-task-item">
              <img class="open-in-progress-closed-task-item-img" src="/orange-info.svg" alt="info_icon">
              <div class="open-in-progress-closed-task-item-text">В работе - x</div>
            </div>
            <div class="d-flex flex-row open-in-progress-closed-task-item">
              <img class="open-in-progress-closed-task-item-img" src="/green-info.svg" alt="info_icon">
              <div class="open-in-progress-closed-task-item-text">Закрыто - x</div>
            </div>
          </div>
        </div>
        <div class="d-flex flex-column add-task-block">
          <div class="current-task-n-add-task-text">
            Добавить задачу
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
  @import "./assets/main.css";
</style>
