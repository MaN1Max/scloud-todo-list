<script setup>
import ListItem from "@/components/ListItem.vue";
import Modal from "@/components/Modal.vue";
import {ref} from "vue";

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
  if(shownAll.value === false)
    anchor.value.scrollIntoView({ behavior: "smooth" });
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
  <div v-show="isEmptyArr()" class="d-flex flex-column task-n-status-block empty-list-text">
    Похоже, что на данный момент задач нет...
  </div>
  <div v-show="!isEmptyArr()" class="d-flex flex-column task-n-status-block">
    <div class="d-flex flex-row task-n-status-block-head-text">
      <div>Задачи</div>
      <div>Статус</div>
    </div>
    <div class="d-flex flex-column task-n-status-list-block">
      <template v-if="isFiveTasksInArr() && !shownAll" v-for="index in 5" :key="index">
        <ListItem :task="props.tasks[index-1]" :openModal="openModal" :currentKey="index-1"/>
      </template>
      <template v-if="(isFiveTasksInArr() && shownAll) || (!isFiveTasksInArr() && shownAll) || (!isFiveTasksInArr() && !shownAll)"
                v-for="(task, index) in props.tasks"
                :key="index">
        <ListItem :task="task" :openModal="openModal" :currentKey="+index"/>
      </template>
    </div>
  </div>
  <button class="d-flex flex-row show-more-tasks-button"
          v-show="isFiveTasksInArr()"
          @click="showHideButton">
    <span v-if="!shownAll">Показать ещё</span>
    <span v-if="shownAll">Скрыть</span>
    <img v-if="!shownAll" class="show-icon" src="/show-hide-icon.svg" alt="show_hide_icon">
    <img v-if="shownAll" class="show-icon" src="/show-hide-icon.svg" alt="show_hide_icon" style="transform: rotate(180deg)">
  </button>
  <Modal :isOpen="modalOpened"
         :closeModal="closeModal"
         :modalCurrentTask="modalCurrentTask"
         :modalCurrentKey="modalCurrentKey"
         :deleteTask="deleteTask"
         :statusChange="statusChange"
         :submitChanges="submitChanges"
         :taskNameChange="taskNameChange"
         :modalCurrentName="modalCurrentName"
         :modalActiveStatus="modalActiveStatus"/>
</template>
