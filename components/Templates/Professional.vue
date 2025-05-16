<template>
  <div class="bg-gradient-to-br from-blue-50 to-blue-200 p-8 rounded-2xl shadow-lg w-full max-w-md mx-auto">
    <div class="flex flex-col items-center mb-6">
      <img v-if="acc.i" :src="acc.i" class="w-24 h-24 rounded-full border-4 border-blue-300 mb-3 object-cover" />
      <h2 class="text-2xl font-extrabold text-blue-900 mb-1">{{ acc.n }}</h2>
      <p class="text-blue-700 text-base mb-2">{{ acc.d }}</p>
    </div>
    <ul class="space-y-3">
      <li v-for="(link, idx) in acc.ls" :key="idx">
        <a :href="link.u" target="_blank" class="flex items-center px-5 py-3 bg-white rounded-lg shadow hover:bg-blue-50 transition">
          <span v-if="link.i" class="mr-3"><icon :name="link.i" class="inline w-5 h-5 text-blue-600" /></span>
          <span class="font-semibold text-blue-900">{{ link.l }}</span>
        </a>
      </li>
    </ul>
  </div>
</template>
<script setup>
const props = defineProps({ acc: { type: Object, required: true } });
</script> 