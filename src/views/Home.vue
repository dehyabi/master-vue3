<template>
  <h2>Home</h2>

  <h3>{{ toDosComplete }}</h3>

  <ToDo :ToDos="ToDoList" @changeToDo="completeToDo" />
</template>

<script setup lang="ts">
import type { ToDoInterface } from "../models/data/ToDo";
import ToDo from "@/components/ToDo.vue";
import { computed, reactive } from "vue";

const ToDoList: ToDoInterface[] = reactive([
  {
    id: 1,
    name: "Watch Movie",
    completed: false,
  },
  {
    id: 2,
    name: "Read Book",
    completed: false,
  },
  {
    id: 3,
    name: "Read News",
    completed: false,
  },
]);

const completeToDo = (id) => {
  console.log("id: ", id);
};

const toDosComplete = computed(() => {
  let all = ToDoList.length;
  let countToDosComplete = 0;

  ToDoList.forEach((ToDo) => {
    if (ToDo.completed) {
      countToDosComplete++;
    }
  });

  return countToDosComplete == all ? "[ All ToDos Complete ]" : "[ No ]";
});
</script>
