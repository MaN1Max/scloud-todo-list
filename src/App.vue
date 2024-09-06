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
            <div class="open-task-block">Открыто - x</div>
            <div class="in-progress-task-block">В работе - x</div>
            <div class="closed-task-block">Закрыто - x</div>
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
