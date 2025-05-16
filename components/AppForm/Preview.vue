<template>
  <div class="h-screen grid place-items-center">
    <div
      class="h-[729px] w-[340px] overflow-y-auto rounded-[3rem] ring-8 ring-slate-800 overflow-hidden"
    >
      <component :is="templateComponent" :acc="data" />
    </div>
  </div>
</template>
<script setup>
import Minimal from '../Templates/Minimal.vue';
import Professional from '../Templates/Professional.vue';

const props = defineProps({
  data: {
    type: Object,
    required: true,
  },
  templateName: {
    type: String,
    default: 'Minimal',
  },
});

const templateMap = {
  Minimal,
  Professional,
};

const templateComponent = computed(() => templateMap[props.templateName] || Minimal);
</script>
<style scoped></style>
