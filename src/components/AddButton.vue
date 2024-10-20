<script setup>
import { computed } from 'vue';
import check from '../assets/check.svg';
import stopwatch from '../assets/stopwatch.svg';

const buttonTypes = {
  stopwatch: 'Add Stopwatch',
  timer: 'Add Timer',
  task: 'Add Task'
}

const iconTypes = {
  stopwatch: stopwatch,
  timer: stopwatch,
  task: check
}

const props = defineProps({
  type: {
    type: String,
    required: true,
    validator: (value) => ['stopwatch', 'timer', 'task'].includes(value)
  }
});

const buttonIcon = computed(() => iconTypes[props.type]);
const buttonText = computed(() => buttonTypes[props.type]);
</script>

<template>
  <button class="button-primary">
    <img :src="buttonIcon" />
    <span>{{ buttonText }}</span>
  </button>
</template>

<style scoped>
button {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  gap: 10px;
  
  width: 100%;
  border-radius: var(--small-radius);
  padding: 10px 0;

  appearance: none;
  background-color: transparent;
  border: 2px solid white;
  box-sizing: border-box;
  color: white;
  cursor: pointer;
  
  font-family: Roobert,-apple-system,BlinkMacSystemFont,"Segoe UI",Helvetica,Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol";
  font-size: 16px;
  font-weight: 600;
  line-height: normal;
  
  min-height: 60px;
  outline: none;
  text-decoration: none;
  transition: all 300ms cubic-bezier(.23, 1, 0.32, 1);
  user-select: none;
  touch-action: manipulation;
}

button:hover {
  color: black;
  background-color: white;
  box-shadow: rgba(0, 0, 0, 0.25) 0 8px 15px;
  border-color: white;
}

button:active {
  box-shadow: none;
  transform: translateY(0);
}

button:hover img {
  filter: invert(100%);
}

img {
  width: 30px;
  height: 30px;
}

span {
  font-size: 1.5rem;
  font-family: "M PLUS 1p", sans-serif;
  font-weight: 400;
  font-style: normal;
}
</style>