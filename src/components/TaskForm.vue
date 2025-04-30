<template>
    <form @submit.prevent="formSubmit">
        <label>
            New Task
            <input 
                v-model="newTask" 
                name="newTask" 
                :aria-invalid="!!error || undefined"
                @input="error = ''"
            >
            <small v-if="error" id="invalid-helper">
                {{ error }}
            </small>
        </label>
        <div class="btn-container">
            <button >Add</button>
        </div>
    </form>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const newTask = ref("");
const error = ref("");

const emit = defineEmits<{
    addTask: [newTask: string]
}>();

const formSubmit = () => {
    if (newTask.value) {
        emit("addTask", newTask.value.trim());
    } else {
        error.value = "Cannot be empty";
    }
    newTask.value = "";
}
</script>

<style scoped>
.btn-container {
  display: flex;
  justify-content: end;
}
</style>