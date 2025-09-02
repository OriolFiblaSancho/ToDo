<template>
    <form @submit.prevent="add">
        <h3>Tarea: </h3><input v-model="taskName"></input>
        <button type="submit">Enter</button>
    </form>
    
</template>

<script setup>
import { ref } from 'vue'

const taskName = ref('')

const emit = defineEmits('add')

function add(){
    emit("add", taskName.value)
    taskName.value = ""
}

</script>

<style scoped>
    * {
        box-sizing: border-boxS;
        padding: 0;
        margin: 0;
    }

    template{
        display: flex;
        flex-direction: row;

        width: auto;
    }

    button{
        margin-left: 5px;
    }
</style>