<script setup>
const props = defineProps({
  task: Object,
  currentKey: Number,
  openModal: Function
});
</script>

<template>
  <div class="d-flex flex-column item-card">
    <div class="d-flex flex-column item-name">{{ props.task.name }}</div>
    <button class="d-flex item-button" @click="openModal(props.task, props.currentKey)">
      {{ props.task.status }}
    </button>
  </div>
</template>

<style scoped>
.d-flex {
  display: flex;
}

.flex-column {
  flex-direction: column;
}

.item-card {
  box-sizing: border-box;
  width: 100%;
  min-height: 132px;
  padding: 24px;
  border-radius: 32px;
  background: #FFFFFF;
  margin-bottom: 24px;
}

.item-name {
  box-sizing: border-box;
  width: 100%;
  font-family: "PT Sans Caption", sans-serif;
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
  color: #333333;
  overflow-wrap: break-word;
}

.item-button {
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 40px;
  margin-top: 20px;
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
</style>
