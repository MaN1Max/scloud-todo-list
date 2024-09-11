<script setup>
import {ref} from "vue";

const props = defineProps({
  tasks: Array
});

const taskToAddName = ref("");
const TASK_STATUS = "Открыт";

const addTask = () => {
  if (taskToAddName.value.trim() === "") {
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
        <img alt="cross_icon" class="add-task-button-img" src="/add-task-cross.svg">
      </button>
      <input v-model="taskToAddName" class="add-task-input" placeholder="Текст" type="search">
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

.add-task-block {
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

.add-task-n-task-input-block {
  justify-content: space-between;
  align-items: center;
  flex-direction: column-reverse;
  margin-top: 24px;
  gap: 15px;
}

.add-task-button {
  width: 100%;
  height: 44px;
  padding: 8px;
  border: none;
  border-radius: 100px;
  background-color: #FF6600;
  cursor: pointer;
}

.add-task-button-img {
  width: 28px;
  height: 20px;
  margin: auto;
}

.add-task-input {
  width: 100%;
  height: 48px;
  border-radius: 100px;
  padding: 12px 16px;
  border: 1px solid #EAEAEA;
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 400;
  font-size: 14px;
  line-height: 24px;
  color: #333333;
}

.add-task-input::placeholder {
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 400;
  font-size: 14px;
  line-height: 24px;
  color: #333333;
}

@media screen and (min-width: 1222px) {
  .add-task-block {
    width: calc(50% - 12px);
  }
}

@media screen and (min-width: 660px) {
  .add-task-button {
    width: 44px;
  }

  .add-task-n-task-input-block {
    flex-direction: row;
  }
}
</style>
