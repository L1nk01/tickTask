<script setup>
import TaskContainer from './components/TaskContainer.vue';
import TimeContainer from './components/TimeContainer.vue';
</script>

<template>
  <h1 id="title">tickTask</h1>
  <div class="app-container">
    <TaskContainer />
    <TimeContainer />
  </div>
</template>

<style scoped>
.app-container {
  min-height: 700px;
  display: flex;
  flex-direction: row;
  flex: 1;
  gap: 30px;
}
</style>
