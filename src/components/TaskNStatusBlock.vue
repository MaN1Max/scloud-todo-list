<script setup>
import ListItem from "@/components/ListItem.vue";
import Modal from "@/components/Modal.vue";
import {ref} from "vue";

const props = defineProps({
  tasks: Array
});

const shownAll = ref(false);

const isFiveTasksInArr = () => {
  return props.tasks.length > 5;
};
const isEmptyArr = () => {
  return props.tasks.length <= 0
};
const showHideButton = () => {
  shownAll.value = !shownAll.value
};
</script>

<template>
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
        <ListItem :task="props.tasks[index-1]"/>
      </template>
      <template v-if="(isFiveTasksInArr() && shownAll) || (!isFiveTasksInArr() && shownAll) || (!isFiveTasksInArr() && !shownAll)" v-for="(task, index) in props.tasks" :key="index">
        <ListItem :task="task"/>
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
  <Modal :isOpen="false"/>
</template>
