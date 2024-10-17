<script setup>
import AddButton from './AddButton.vue';
import TaskItem from './TaskItem.vue';
</script>

<template>
  <div class="task-container">
    <div class="button-container">
      <AddButton type="task" />
    </div>

    <div class="tasks">
      <TaskItem />
      <TaskItem />
    </div>
  </div>
</template>

<style scoped>
.task-container {
  width: 100%;
  min-height: 100%;
  border: 2px solid white;
  border-radius: var(--radius);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 25px;
  gap: 20px;
}

.button-container {
  width: 100%;
}

.tasks {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>