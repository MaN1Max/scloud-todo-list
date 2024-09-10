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
    } else if (task2.status === 'Открыт' && task1.status !== 'Открыт') {
      return 1;
    } else if (task1.status > task2.status)
      return 1;
    else return -1;
  });
};

watchEffect(() => {
  if (tasks.value) {
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
      <TaskDesk :tasks="tasks"/>
    </div>
    <div class="footer-block"></div>
  </div>
</template>

<style scoped>
.d-flex {
  display: flex;
}

.flex-column {
  flex-direction: column;
}

.upper-bg-frame {
  width: auto;
  height: auto;
  background: #F4F4F4;
}

.content-container {
  margin: 0 auto;
  max-width: 1200px;
  width: 100%;
  padding: 0 54px;
}

.header-text {
  font-family: 'Montserrat', sans-serif;
  font-weight: 700;
  font-size: 32px;
  line-height: 40px;
  text-align: left;
  margin-top: 64px;
  color: #333333;
}

.current-task-n-add-task-block {
  flex-direction: column;
  gap: 24px;
  margin-top: 48px;
}

.footer-block {
  box-sizing: border-box;
  width: 100%;
  height: 144px;
  margin-top: 64px;
  padding: 60px 60px 40px 60px;
  border-radius: 48px 48px 0 0;
  background: #BBB8B6;
}

@media screen and (min-width: 1222px) {
  .current-task-n-add-task-block {
    flex-direction: row;
  }
}
</style>
