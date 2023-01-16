<template>
  <TodoForm @response="addTask" />
  <TabGroup>
    <TabList class="flex space-x-1 rounded-xl p-2 bg-gray-400">
      <Tab
        v-for="category in Object.keys(todoList)"
        as="template"
        :key="category"
        v-slot="{ selected }"
      >
        <button
          :class="[
            'w-full rounded-lg py-2.5 text-base font-medium leading-5',
            'focus:outline-none',
            selected
              ? 'bg-gray-500 shadow text-purple-300'
              : 'text-purple-600 hover:bg-white/[0.40] hover:text-white',
          ]"
        >
          {{ category }}
        </button>
      </Tab>
    </TabList>

    <TabPanels class="mt-2">
      <TabPanel
        v-for="(posts, idx) in Object.values(todoList)"
        :key="idx"
        :class="['rounded-xl p-2 h-full flex bg-gray-400']"
      >
        <ul class="w-full flex flex-col gap-1">
          <li
            v-for="post in posts"
            :key="post.id"
            class="relative rounded-xl p-3 bg-gray-500 text-purple-400 w-full"
          >
            <h3 class="text-sm font-medium leading-5">
              {{ post.title ? post.title : "Sem Tarefas" }}
            </h3>

            <ul
              class="mt-1 flex space-x-1 text-xs font-normal leading-4 text-white"
            >
              <li>{{ post.date }}</li>
            </ul>

            <a
              href="#"
              :class="[
                'absolute inset-0 rounded-md',
                'focus:z-10 focus:outline-none',
              ]"
            />
          </li>
        </ul>
      </TabPanel>
    </TabPanels>
  </TabGroup>
</template>

<script setup>
import { onBeforeMount, ref } from "vue";
import TodoForm from "./TodoForm.vue";
import { TabGroup, TabList, Tab, TabPanels, TabPanel } from "@headlessui/vue";

let todoList = ref({
  Tarefas: [],
  Concluidas: [],
});

onBeforeMount(() => {
  todoList.value.Tarefas = [
    {
      id: 1,
      title: "Não há Tarefas !",
      date: "",
    },
  ];
  todoList.value.Concluidas = [
    {
      id: 1,
      title: "Não há Tarefas !",
      date: "",
    },
  ];
});


const inputValidation = (param) => {
  if (!param) {
    alert('Tarefa em branco !')
    return;
  }
  if (todoList.value.Tarefas.some((item) => item.title === param)){
    alert("Tarefa já existe !");
    return;
  } 

  return true;
};

const addTask = (response) => {
  if (inputValidation(response)) {
    
    todoList.value.Tarefas.push({
      id: todoList.value.Tarefas.length,
      title: response,
      date: new Date().toDateString(),
    });

    todoList.value.Tarefas = todoList.value.Tarefas.filter(
      ({ title }) => title !== "Não há Tarefas !"
    );
  }
};
</script>
