<script setup lang="ts">
import { defineEmits } from 'vue';
import type { TaskFilter } from '../types';

const props = defineProps<{
    filter: TaskFilter
    currentFilter: TaskFilter
}>();

const emits = defineEmits<{
    filterEmit: [filterVal: TaskFilter];
}>();
</script>
<template>
    <button 
        :class="{'contrast': filter == currentFilter}" 
        class="secondary" 
        @click="emits('filterEmit', filter)"
    >{{ props.filter }}</button>
</template>

<style scoped>
button {
    text-transform: capitalize;
}
</style>