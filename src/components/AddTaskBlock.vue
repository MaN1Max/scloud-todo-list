<script setup>
import {ref} from "vue";

const props = defineProps({
  tasks: Array
});

const taskToAddName = ref("");
const TASK_STATUS = "Открыт";

const addTask = () => {
  if(taskToAddName.value.trim() === "")
  {
    taskToAddName.value = "";
    return;
  }
  props.tasks.push({
    name: taskToAddName.value,
    status: TASK_STATUS
  });
  taskToAddName.value = "";
};
</script>

<template>
  <div class="d-flex flex-column add-task-block">
    <div class="current-task-n-add-task-text">
      Добавить задачу
    </div>
    <div class="d-flex flex-row add-task-n-task-input-block">
      <button class="d-flex add-task-button" @click="addTask()">
        <img class="add-task-button-img" src="/add-task-cross.svg" alt="cross_icon">
      </button>
      <input class="add-task-input" type="search" placeholder="Текст" v-model="taskToAddName">
    </div>
  </div>
</template>
