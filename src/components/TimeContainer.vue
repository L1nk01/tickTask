<script setup>
import AddButton from './AddButton.vue';
</script>

<template>
  <div class="time-container">
    <div class="button-container">
      <AddButton type="stopwatch" />
      <AddButton type="timer" />
    </div>
  </div>
</template>

<style scoped>
.time-container {
  width: 100%;
  min-height: 100%;
  border: 2px solid white;
  border-radius: var(--radius);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 25px;
}

.button-container {
  width: 100%;
  display: flex;
  flex-direction: row;
  gap: 25px;
}
</style>