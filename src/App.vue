<script setup lang="ts">
import { computed, ref } from 'vue';
import TaskForm from './components/TaskForm.vue';
import type { Task, TaskFilter } from './types';
import TaskList from './components/TaskList.vue';
import FilterButton from './components/FilterButton.vue';

const message = ref("Todo App");
const tasks = ref<Task[]>([]);
const filter = ref<TaskFilter>("all");

const doneCount = computed(() => tasks
  .value
  .reduce((total, task) => task.done ? total + 1 : total, 0));

const filteredTasks = computed(() => {
  if (filter.value == "all") return tasks.value;
  if (filter.value == "done") return tasks.value.filter(task => task.done);
  if (filter.value == "todo") return tasks.value.filter(task => !task.done);
  return tasks.value;
});

const addTask = (newTask: string) => {
  tasks.value.push({
    id: crypto.randomUUID(),
    title: newTask,
    done: false
  })
}

const toggleDone = (taskId: string) => {
  const task = tasks.value.find((task) => task.id == taskId);
  if (task) task.done = !task.done
}

const removeTask = (taskId: string) => {
  tasks.value = tasks.value.filter(task => task.id != taskId)
}

const setFilter = (filterVal: TaskFilter) => {
  filter.value = filterVal;
}

</script>

<template>
  <main>
    <h1>{{ message }}</h1>
    <TaskForm @add-task="addTask"/>
    <h3 v-if="!tasks.length">No tasks yet, add one.</h3>
    <h3 v-else>You have completed {{ doneCount }}/{{ tasks.length }} tasks.</h3>
    <div v-if="tasks.length" class="btn-container">
      <FilterButton :currentFilter="filter" filter="all" @filter-emit="setFilter"/>
      <FilterButton :currentFilter="filter" filter="done" @filter-emit="setFilter"/>
      <FilterButton :currentFilter="filter" filter="todo" @filter-emit="setFilter"/>
    </div>
    <TaskList :tasks="filteredTasks" @toggle-done="toggleDone" @remove-task="removeTask"/>
  </main>
</template>

<style scoped>
main {
  max-width: 800px;
  margin: 1rem auto;
}

.btn-container {
  display: flex;
  justify-content: end;
  gap: 0.5rem;
}
</style>
