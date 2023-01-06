<template>
  <div
    class="w-full h-full flex flex-col justify-center items-center bg-gray-900"
  >
    <div class="p-3 w-[30rem] h-96 bg-gray-900 rounded-xl space-y-2 text-white">
      <!-- <TodoForm /> -->
      <TodoTabs />
    </div>
  </div>
</template>

<script setup>
import TodoTabs from "./components/TodoTabs.vue";
// import TodoForm from "./components/TodoForm.vue";
</script>
<style scoped></style>
