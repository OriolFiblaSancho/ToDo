<template>
  <h2>TO-DO APP</h2>
  <TaskForm @add="addTask"></TaskForm>
  <TaskList 
    :tasks="tasks" 
    @complete="completeTask"
    @delete="deleteTask"
  />
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import TaskForm from "./components/TaskForm.vue";
import TaskList from "./components/TaskList.vue";

const tasks = ref([]);

onMounted(() => {
  tasks.value = JSON.parse(localStorage.getItem("tasks") || "[]");
});

function addTask(taskNameValue){
  const task = {
    id: Date.now(),
    name: taskNameValue,
    completed: false
  };
  tasks.value.push(task);
  localStorage.setItem("tasks", JSON.stringify(tasks.value));
}

function completeTask(id){
  const task = tasks.value.find(t => t.id === id);
  task.completed = true;
  localStorage.setItem("tasks", JSON.stringify(tasks.value));
}

function deleteTask(id){
  tasks.value = tasks.value.filter(t => t.id !== id);
  localStorage.setItem("tasks", JSON.stringify(tasks.value));
}

</script>
<style scoped></style>
