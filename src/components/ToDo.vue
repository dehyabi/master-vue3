<template>
  <div class="mt-10 mb-5">ToDo List</div>
  <div>City: {{ city }}</div>

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
import { inject } from 'vue';
import type { ToDoInterface } from "../models/data/ToDo";
defineProps<{ ToDos: ToDoInterface[] }>();

const emit = defineEmits<{ (e: "changeToDo", id: number): any }>();

const completeToDo = (id) => {
  emit("changeToDo", id);
};

const city = inject('testCity');
// const city = inject('testCity', 'default value');

console.log(`city: ${city.value}`);
</script>
