<template>
  <div class="mt-10 mb-5">ToDo List</div>

  <ul v-for="ToDo in ToDos">
    <li>
      - {{ ToDo.name }}
      <input
        type="checkbox"
        v-model="ToDo.completed"
        @click="completeToDo(ToDo.id)"
      />
    </li>
  </ul>
</template>

<script setup lang="ts">
import type { ToDoInterface } from "../models/data/ToDo";
defineProps<{ ToDos: ToDoInterface[] }>();

const emit = defineEmits<{ (e: "changeToDo", id: number): any }>();

const completeToDo = (id) => {
  emit("changeToDo", id);
};
</script>
