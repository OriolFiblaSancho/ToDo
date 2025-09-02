<template>
  <div id="item">
    <h3>{{ task.name }} - {{ task.completed ? 'COMPLETADA' : 'NO COMPLETADA' }}</h3>
    <button @click="completeTask">COMPLETAR</button>
    <button @click="deleteTask">ELIMINAR</button>
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from 'vue';
const props = defineProps<{ task: { id: number | string } }>();
const emit = defineEmits(['complete', 'delete']);

function completeTask(){
    emit("complete", props.task.id);
}

function deleteTask(){
    emit("delete", props.task.id);
}

</script>

<style>
    #item{
        background-color: aqua;
        display: flex;
        flex-direction: row;
        margin-top: 30px;
        padding-left: 10px;
        gap:10px;
    }
</style>