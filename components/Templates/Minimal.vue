<template>
  <div class="p-6 bg-white rounded-lg shadow w-full max-w-md mx-auto">
    <div class="flex flex-col items-center">
      <img v-if="acc.i" :src="acc.i" class="w-20 h-20 rounded-full mb-4 object-cover" />
      <h2 class="text-xl font-bold mb-1">{{ acc.n }}</h2>
      <p class="text-gray-500 text-sm mb-4">{{ acc.d }}</p>
    </div>
    <ul class="space-y-2">
      <li v-for="(link, idx) in acc.ls" :key="idx">
        <a :href="link.u" target="_blank" class="block px-4 py-2 bg-slate-100 rounded hover:bg-slate-200 transition">
          <span v-if="link.i" class="mr-2"><icon :name="link.i" class="inline w-4 h-4" /></span>
          {{ link.l }}
        </a>
      </li>
    </ul>
  </div>
</template>
<script setup>
const props = defineProps({ acc: { type: Object, required: true } });
</script> 