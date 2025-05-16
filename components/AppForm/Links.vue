<template>
  <base-form-section title="Links" description="Add some links here">
    <template #helpertext>
      <p class="mt-1 text-xs text-gray-600">
        Icon keys can be found in
        <a class="underline" href="https://icones.js.org/"
          >https://icones.js.org/</a
        >.
      </p>
    </template>
    <div class="shadow sm:overflow-hidden sm:rounded-md">
      <div class="space-y-6 bg-white px-4 py-5 sm:p-6">
        <div class="grid grid-cols-2 gap-4">
          <div class="col-span-2">
            <label class="block text-sm font-medium text-gray-700 mb-2">Links (Drag to reorder)</label>
            <draggable :modelValue="modelValue" @update:modelValue="onDrag" item-key="l" class="space-y-2" handle=".drag-handle">
              <template #item="{ element, index }">
                <div class="flex items-center space-x-2 bg-slate-50 p-2 rounded">
                  <span class="drag-handle cursor-move text-gray-400">☰</span>
                  <input v-model="element.l" placeholder="Label" class="flex-1 px-2 py-1 rounded border border-gray-300" />
                  <input v-model="element.i" placeholder="Icon Key" class="w-32 px-2 py-1 rounded border border-gray-300" />
                  <input v-model="element.u" placeholder="URL" class="flex-1 px-2 py-1 rounded border border-gray-300" />
                  <button @click.prevent="removeLink(index)" class="text-red-500 font-bold ml-2">✕</button>
                </div>
              </template>
            </draggable>
            <button @click.prevent="addLink" class="mt-2 px-3 py-1 bg-blue-100 rounded text-blue-800 font-semibold">Add Link</button>
          </div>
        </div>
      </div>
    </div>
  </base-form-section>
</template>
<script setup>
import draggable from 'vuedraggable';
const props = defineProps({
  modelValue: Array
});
const emit = defineEmits(['update:modelValue']);
function addLink() {
  emit('update:modelValue', [...props.modelValue, { l: '', i: '', u: '' }]);
}
function removeLink(idx) {
  const links = [...props.modelValue];
  links.splice(idx, 1);
  emit('update:modelValue', links);
}
function onDrag(newValue) {
  emit('update:modelValue', newValue);
}
</script>
<style scoped>
.flip-list-move {
  transition: transform 0.5s;
}
.no-move {
  transition: transform 0s;
}
.ghost {
  opacity: 0.5;
  background: #c8ebfb;
}
.list-group {
  min-height: 20px;
}
.list-group-item {
  cursor: move;
}
.list-group-item i {
  cursor: pointer;
}
</style>
