<script setup>

const props = defineProps({
  tasks: Array
});

const dragStart = (event, index) => {
  event.dataTransfer.setData("index", index);
};
const drop = (event, newStatus) => {
  const index = event.dataTransfer.getData("index");
  props.tasks[index].status = newStatus;
};
</script>

<template>
  <div class="is-task-desk-shown">
    <h2 class="d-flex header-text">Доска задач</h2>
    <div class="d-flex flex-row task-desk-block">
      <div class="d-flex flex-column task-desk-item-block">
        <div class="d-flex task-desk-item-label-wrapper">
          <div class="d-flex task-desk-item-label">Открыто</div>
        </div>
        <div class="d-flex flex-column task-desk-item-list-block" @drop="drop($event, 'Открыт')" @dragover.prevent
             @dragenter.prevent>
          <template v-for="(task, index) in props.tasks" :key="index">
            <div v-if="task.status === 'Открыт'" class="task-desk-item-in-list" draggable="true"
                 @dragstart="dragStart($event, index)">
              {{ task.name }}
            </div>
          </template>
        </div>
      </div>
      <div class="d-flex flex-column task-desk-item-block">
        <div class="d-flex task-desk-item-label-wrapper">
          <div class="d-flex task-desk-item-label">В работе</div>
        </div>
        <div class="d-flex flex-column task-desk-item-list-block" @drop="drop($event, 'В работе')" @dragover.prevent
             @dragenter.prevent>
          <template v-for="(task, index) in props.tasks" :key="index">
            <div v-if="task.status === 'В работе'" class="task-desk-item-in-list" draggable="true"
                 @dragstart="dragStart($event, index)">
              {{ task.name }}
            </div>
          </template>
        </div>
      </div>
      <div class="d-flex flex-column task-desk-item-block">
        <div class="d-flex task-desk-item-label-wrapper">
          <div class="d-flex task-desk-item-label">Закрыто</div>
        </div>
        <div class="d-flex flex-column task-desk-item-list-block" @drop="drop($event, 'Закрыт')" @dragover.prevent
             @dragenter.prevent>
          <template v-for="(task, index) in props.tasks" :key="index">
            <div v-if="task.status === 'Закрыт'" class="task-desk-item-in-list" draggable="true"
                 @dragstart="dragStart($event, index)">
              {{ task.name }}
            </div>
          </template>
        </div>
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

.header-text {
  width: 100%;
  font-family: 'Montserrat', sans-serif;
  font-weight: 700;
  font-size: 32px;
  line-height: 40px;
  text-align: left;
  margin-top: 64px;
  color: #333333;
}

.task-desk-block {
  justify-content: space-between;
  width: 100%;
  margin-top: 48px;
  gap: 16px;
}

.task-desk-item-block {
  width: 100%;
  min-width: 250px;
}

.task-desk-item-label-wrapper {
  width: 100%;
}

.task-desk-item-label {
  box-sizing: border-box;
  justify-content: center;
  align-items: center;
  width: fit-content;
  height: 48px;
  padding: 5px 24px 5px 24px;
  border-radius: 39px;
  background: #F4F4F4;
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 700;
  font-size: 20px;
  line-height: 28px;
  color: #333333;
}

.task-desk-item-list-block {
  box-sizing: border-box;
  width: 100%;
  min-height: 280px;
  padding: 16px;
  gap: 16px;
  margin-top: 24px;
  border-radius: 24px;
  background: #EAEAEA80;
}

.task-desk-item-in-list {
  box-sizing: border-box;
  width: 100%;
  min-height: 72px;
  padding: 24px 32px 24px 32px;
  border-radius: 24px;
  background: #FFFFFF;
  border: 2px solid #EAEAEA;
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
  color: #333333;
  overflow-wrap: break-word;
  cursor: pointer;
}

@media screen and (max-width: 1221px) {
  .is-task-desk-shown {
    display: none;
  }
}
</style>
