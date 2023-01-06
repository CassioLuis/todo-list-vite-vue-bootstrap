<template>
  <div
    class="w-full h-full flex justify-center bg-gray-900"
  >
    <div class="p-3 w-[30rem] h-96 bg-gray-900 rounded-xl space-y-2 text-white pt-20">
      <TodoTabs />
    </div>
  </div>
</template>

<script setup>
import TodoTabs from "./components/TodoTabs.vue";
</script>
<style scoped></style>
