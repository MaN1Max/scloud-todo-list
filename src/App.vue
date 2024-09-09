<script setup>
import CurrentTaskBlock from "@/components/CurrentTaskBlock.vue";
import AddTaskBlock from "@/components/AddTaskBlock.vue";
import TaskNStatusBlock from "@/components/TaskNStatusBlock.vue";
import TaskDesk from "@/components/TaskDesk.vue";
import {onMounted, ref, watchEffect} from "vue";

const tasks = ref(null);

const sortTasks = (tasks) => {
  tasks.sort((task1, task2) => {
    if (task1.status === task2.status) {
      return 0;
    }
    if (task1.status === 'Открыт' && task2.status !== 'Открыт') {
      return -1;
    }
    else if (task2.status === 'Открыт' && task1.status !== 'Открыт') {
      return 1;
    }
    else if (task1.status > task2.status)
      return 1;
    else return -1;
  });
};

watchEffect(() => {
  if (tasks.value)
  {
    sortTasks(tasks.value);
    localStorage.setItem("tasks", JSON.stringify(tasks.value));
  }
});

onMounted(() => {
  tasks.value = JSON.parse(localStorage.getItem("tasks")) || [];
});
</script>

<template>
  <div v-if="tasks">
    <div class="d-flex upper-bg-frame">
      <div class="d-flex flex-column content-container">
        <h1 class="header-text">ToDo List Scloud</h1>
        <div class="d-flex flex-row current-task-n-add-task-block">
          <CurrentTaskBlock :tasks="tasks"/>
          <AddTaskBlock :tasks="tasks"/>
        </div>
        <TaskNStatusBlock :tasks="tasks"/>
      </div>
    </div>
    <div class="d-flex flex-column content-container">
      <TaskDesk/>
    </div>
    <div class="footer-block"></div>
  </div>
</template>
