<template>
  <task-item 
    v-for="task in tasks"
    :task="task"
    @complete="onComplete"
    @delete="onDelete"
  />
</template>

<script setup lang="ts">
import TaskItem from "./TaskItem.vue";
const emit = defineEmits(['complete', 'delete']);

defineProps({
  tasks: {
    type: Array,
    required: true
  }
});

function onComplete(id: number | string) {
  emit('complete', id);
}

function onDelete(id: number | string) {
  emit('delete', id);
}
</script>