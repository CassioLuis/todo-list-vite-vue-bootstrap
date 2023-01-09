<template>
  <form @submit.prevent="eventEmit" class="w-full grid grid-cols-4">
    <input
      v-model="message"
      type="text"
      class="px-4 py-3 col-span-3 rounded-tl-xl rounded-bl-xl outline-none bg-zinc-100 placeholder:text-zinc-300 text-black"
      placeholder="Digite uma tarefa"
    />
    <button
      @click.prevent="eventEmit"
      type="button"
      class="bg-zinc-500 col-span-1 hover:bg-zinc-600 transition-all text-purple-400 font-bold px-3 py-2 rounded-tr-xl rounded-br-xl text-xs"
    >
      ADICIONAR
    </button>
  </form>
</template>
<script setup>
import { ref } from 'vue';

const message = ref('')

const emit = defineEmits(['response'])

const eventEmit = () => {
  emit('response', message.value);
  message.value = ''
}
</script>
