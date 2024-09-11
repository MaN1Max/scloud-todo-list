<script setup>
import ListItem from "@/components/ListItem.vue";
import Modal from "@/components/Modal.vue";
import {ref} from "vue";
import ListItemMobile from "@/components/ListItemMobile.vue";

const props = defineProps({
  tasks: Array
});

const anchor = ref();

const shownAll = ref(false);
const modalOpened = ref(false);
const modalCurrentKey = ref(null);
const modalCurrentTask = ref(null);
const modalCurrentStatus = ref("");
const modalCurrentName = ref("");
const modalActiveStatus = ref("");

const isFiveTasksInArr = () => {
  return props.tasks.length > 5;
};
const isEmptyArr = () => {
  return props.tasks.length <= 0
};
const showHideButton = () => {
  shownAll.value = !shownAll.value;
  if (shownAll.value === false)
    anchor.value.scrollIntoView({behavior: "smooth"});
};
const openModal = (task, key) => {
  modalCurrentTask.value = task;
  modalCurrentKey.value = key;
  modalActiveStatus.value = task.status;
  modalCurrentName.value = task.name;
  modalOpened.value = true;
};
const closeModal = () => {
  modalOpened.value = false;
};
const deleteTask = () => {
  props.tasks.splice(modalCurrentKey.value, 1);
  closeModal();
};
const statusChange = (status) => {
  modalCurrentStatus.value = status;
  modalActiveStatus.value = status;
};
const taskNameChange = (event) => {
  modalCurrentName.value = event.target.value;
};
const submitChanges = () => {
  modalCurrentTask.value.status = modalCurrentStatus.value || modalActiveStatus.value;
  modalCurrentTask.value.name = modalCurrentName.value;
  props.tasks[modalCurrentKey.value] = modalCurrentTask.value;
  closeModal();
};
</script>

<template>
  <div ref="anchor"></div>
  <div class="d-flex flex-column task-n-status-block-desktop">
    <div v-show="isEmptyArr()" class="d-flex flex-column task-n-status-block empty-list-text">
      Похоже, что на данный момент задач нет...
    </div>
    <div v-show="!isEmptyArr()" class="d-flex flex-column task-n-status-block">
      <div class="d-flex flex-row task-n-status-block-head-text">
        <div>Задачи</div>
        <div>Статус</div>
      </div>
      <div class="d-flex flex-column task-n-status-list-block">
        <template v-for="index in 5" v-if="isFiveTasksInArr() && !shownAll" :key="index">
          <ListItem :currentKey="index-1" :openModal="openModal" :task="props.tasks[index-1]"/>
        </template>
        <template
            v-for="(task, index) in props.tasks"
            v-if="(isFiveTasksInArr() && shownAll) || (!isFiveTasksInArr() && shownAll) || (!isFiveTasksInArr() && !shownAll)"
            :key="index">
          <ListItem :currentKey="+index" :openModal="openModal" :task="task"/>
        </template>
      </div>
    </div>
  </div>
  <div class="flex-column task-n-status-block-mobile">
    <div class="header-text">Задачи</div>
    <div v-show="isEmptyArr()" class="d-flex flex-column task-n-status-block empty-list-text">
      Похоже, что на данный момент задач нет...
    </div>
    <div class="flex-column task-n-status-list-block-mobile">
      <template v-for="index in 5" v-if="isFiveTasksInArr() && !shownAll" :key="index">
        <ListItemMobile :currentKey="index-1" :openModal="openModal" :task="props.tasks[index-1]"/>
      </template>
      <template
          v-for="(task, index) in props.tasks"
          v-if="(isFiveTasksInArr() && shownAll) || (!isFiveTasksInArr() && shownAll) || (!isFiveTasksInArr() && !shownAll)"
          :key="index">
        <ListItemMobile :currentKey="+index" :openModal="openModal" :task="task"/>
      </template>
    </div>
  </div>
  <button v-show="isFiveTasksInArr()"
          class="d-flex flex-row show-more-tasks-button"
          @click="showHideButton">
    <span v-if="!shownAll">Показать ещё</span>
    <span v-if="shownAll">Скрыть</span>
    <img v-if="!shownAll" alt="show_hide_icon" class="show-icon" src="/show-hide-icon.svg">
    <img v-if="shownAll" alt="show_hide_icon" class="show-icon" src="/show-hide-icon.svg"
         style="transform: rotate(180deg)">
  </button>
  <Modal :closeModal="closeModal"
         :deleteTask="deleteTask"
         :isOpen="modalOpened"
         :modalActiveStatus="modalActiveStatus"
         :modalCurrentKey="modalCurrentKey"
         :modalCurrentName="modalCurrentName"
         :modalCurrentTask="modalCurrentTask"
         :statusChange="statusChange"
         :submitChanges="submitChanges"
         :taskNameChange="taskNameChange"/>
</template>

<style scoped>
.d-flex {
  display: flex;
}

.flex-column {
  flex-direction: column;
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

.task-n-status-block {
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  padding: 40px 40px;
  margin-top: 60px;
  margin-bottom: 40px;
  border-radius: 48px;
  background-color: #FFFFFF;
}

.task-n-status-block-mobile {
  display: none;
}

.empty-list-text {
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 700;
  font-size: 18px;
  line-height: 26px;
  text-align: center;
  color: #333333;
}

.task-n-status-block-head-text {
  justify-content: space-between;
  margin-right: 25px;
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 700;
  font-size: 18px;
  line-height: 26px;
  text-align: center;
  color: #333333;
}

.task-n-status-list-block {
  width: 100%;
  height: 100%;
  margin-top: 14px;
}

.task-n-status-list-block-mobile {
  display: none;
  width: 100%;
  height: 100%;
  margin-top: 48px;
  margin-bottom: 40px;
}

.show-more-tasks-button {
  align-items: center;
  justify-content: center;
  width: 193px;
  height: 48px;
  margin-bottom: 40px;
  padding: 12px 32px 12px 32px;
  border-radius: 50px;
  border: 2px solid #FF6600;
  background-color: #FFFFFF;
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 700;
  font-size: 14px;
  line-height: 24px;
  color: #FF6600;
  cursor: pointer;
}

.show-icon {
  margin-left: 12px;
}

@media screen and (max-width: 659px) {
  .task-n-status-block-desktop {
    display: none;
  }

  .task-n-status-block-mobile {
    display: flex;
  }

  .task-n-status-list-block-mobile {
    display: flex;
  }
}
</style>
