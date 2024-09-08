<script setup>
import CurrentTaskBlock from "@/components/CurrentTaskBlock.vue";
import AddTaskBlock from "@/components/AddTaskBlock.vue";
import TaskNStatusBlock from "@/components/TaskNStatusBlock.vue";
import TaskDesk from "@/components/TaskDesk.vue";
import {ref, watchEffect} from "vue";

const tasks = ref(JSON.parse(localStorage.getItem("tasks")) || []);

watchEffect(() => {
  localStorage.setItem("tasks", JSON.stringify(tasks.value));
});
</script>

<template>
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
</template>
