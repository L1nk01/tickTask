<script setup>
import check from '../assets/check.svg';
import check_blank from '../assets/check_blank.svg';
import pencil from '../assets/pencil.svg';
import bin from '../assets/bin.svg';
import right_arrow from '../assets/right_arrow.svg';
import { ref } from 'vue';

const isChecked = ref(false);
const isOpen = ref(false);
const isEditable = ref(false);
const taskTitle = ref('Nombre de la tarea');
const taskDescription = ref('Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam eu tellus iaculis nisi condimentum fringilla. Nulla facilisi. Vivamus sed lorem quis lacus feugiat scelerisque at sed lectus. Proin sollicitudin bibendum risus, non vehicula nulla tristique sed. Phasellus consectetur maximus arcu et blandit');

const toggleCheck = () => {
  isChecked.value = !isChecked.value;
}

const toggleOpen = () => {
  isOpen.value = !isOpen.value;
}

const toggleEdit = () => {
  isEditable.value = !isEditable.value;
}

const handleEditAndOpen = () => {
  toggleEdit();
  if (!isOpen.value) toggleOpen();
}

const saveTaskInLocalStorage = () => {
  localStorage.setItem('taskTitle', taskTitle.value);
  localStorage.setItme('taskDescription', taskDescription.value);
}

const getTaskFromLocalStorage = () => {
  taskTitle.value = localStorage.getItem('taskTitle') || 'Name';
  taskDescription.value = localStorage.getItem('taskDescription') || 'Description';
}

const getTaskTitle = () => {
  return taskTitle.value;
}

const getTaskDescription = () => {
  return taskDescription.value;
}
</script>

<template>
  <div class="task">
    <div class="top">
      <div class="left-side">
        <img @click="toggleCheck" :src="isChecked ? check : check_blank" />
        <span id="task-title" @click.stop :contenteditable="isEditable">{{ taskTitle }}</span>
      </div>

      <div class="right-side">
        <img :src="bin" />
        <img @click="handleEditAndOpen" :src="pencil" />
        <img @click="toggleOpen" :class="{ 'task-opened': isOpen }" :src="right_arrow" />
      </div>
    </div>

    <div :class="{ 'show': isOpen }">
      <span id="task-description" @click.stop :class="{ 'description': true, 'show': isOpen }" :contenteditable="isEditable">{{ taskDescription }}</span>
    </div>
  </div>
</template>

<style scoped>
.task{
  max-width: 100%;
  display: flex;
  flex-direction: column;
  border: 2px solid white;
  border-radius: var(--small-radius);
  padding: 15px;
  justify-content: space-between;
  transition: all 300ms cubic-bezier(.23, 1, 0.32, 1);
  user-select: none;
  touch-action: manipulation;
}

.task:hover {
  background-color: white;
  border-color: white;
  color: black;
  cursor: pointer;
}

.task:hover img {
  filter: invert(100%);
}

.top {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.left-side, .right-side {
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 15px;
}

img {
  width: 26px;
  height: 26px;
  transition: all 300ms cubic-bezier(.23, 1, 0.32, 1);
}

span {
  font-size: 1.2rem;
}

[contenteditable] {
  border: none;
  outline: none;
}

#task-description {
  width: 100%;
  height: 100%;
}

img.task-opened {
  transform: rotate(90deg);
  transition: all 300ms cubic-bezier(.23, 1, 0.32, 1);
}

.description {
  display: none;
}

div.show {
  /* margin-top: 10px; */
}

span.show {
  display: inline;
}
</style>