<template>
  <base-form-section
    title="Social Links"
    description="Add some social media links"
  >
    <div class="shadow sm:overflow-hidden sm:rounded-md">
      <div class="grid grid-cols-2 gap-8 bg-white px-4 py-5 sm:p-6">
        <div>
          <label for="facebook" class="block text-sm font-medium text-gray-700"
            >Facebook</label
          >
          <div class="mt-1 flex rounded-md shadow-sm">
            <span
              class="inline-flex items-center rounded-l-md border border-r-0 border-gray-300 bg-gray-50 px-3 text-sm text-gray-500"
            >
              <icon name="ph:facebook-logo-duotone" class="w-5 h-5" />
            </span>
            <input
              type="search"
              name="facebook"
              id="facebook"
              :value="facebook"
              @input="$emit('update:facebook', $event.target.value)"
              class="block w-full flex-1 rounded-none rounded-r-md border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm"
              placeholder="https://fb.com/elonmusk"
            />
          </div>
        </div>
        <div>
          <label for="twitter" class="block text-sm font-medium text-gray-700"
            >Twitter</label
          >
          <div class="mt-1 flex rounded-md shadow-sm">
            <span
              class="inline-flex items-center rounded-l-md border border-r-0 border-gray-300 bg-gray-50 px-3 text-sm text-gray-500"
            >
              <icon name="ph:twitter-logo-duotone" class="w-5 h-5" />
            </span>
            <input
              type="search"
              name="twitter"
              id="twitter"
              :value="twitter"
              @input="$emit('update:twitter', $event.target.value)"
              class="block w-full flex-1 rounded-none rounded-r-md border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm"
              placeholder="https://twitter.com/elonmusk"
            />
          </div>
        </div>
        <div>
          <label for="instagram" class="block text-sm font-medium text-gray-700"
            >Instagram</label
          >
          <div class="mt-1 flex rounded-md shadow-sm">
            <span
              class="inline-flex items-center rounded-l-md border border-r-0 border-gray-300 bg-gray-50 px-3 text-sm text-gray-500"
            >
              <icon name="ph:instagram-logo-duotone" class="w-5 h-5" />
            </span>
            <input
              type="search"
              name="instagram"
              id="instagram"
              :value="instagram"
              @input="$emit('update:instagram', $event.target.value)"
              class="block w-full flex-1 rounded-none rounded-r-md border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm"
              placeholder="https://instagram.com/elonmusk"
            />
          </div>
        </div>
        <div>
          <label for="instagram" class="block text-sm font-medium text-gray-700"
            >Github</label
          >
          <div class="mt-1 flex rounded-md shadow-sm">
            <span
              class="inline-flex items-center rounded-l-md border border-r-0 border-gray-300 bg-gray-50 px-3 text-sm text-gray-500"
            >
              <icon name="ph:github-logo-duotone" class="w-5 h-5" />
            </span>
            <input
              type="search"
              name="github"
              id="github"
              :value="github"
              @input="$emit('update:github', $event.target.value)"
              class="block w-full flex-1 rounded-none rounded-r-md border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm"
              placeholder="https://github.com/elonmusk"
            />
          </div>
        </div>
        <div>
          <label for="instagram" class="block text-sm font-medium text-gray-700"
            >Telegram</label
          >
          <div class="mt-1 flex rounded-md shadow-sm">
            <span
              class="inline-flex items-center rounded-l-md border border-r-0 border-gray-300 bg-gray-50 px-3 text-sm text-gray-500"
            >
              <icon name="ph:telegram-logo-duotone" class="w-5 h-5" />
            </span>
            <input
              type="search"
              name="telegram"
              id="telegram"
              :value="telegram"
              @input="$emit('update:telegram', $event.target.value)"
              class="block w-full flex-1 rounded-none rounded-r-md border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm"
              placeholder="https://t.me/elonmusk"
            />
          </div>
        </div>
        <div>
          <label for="instagram" class="block text-sm font-medium text-gray-700"
            >Linkedin</label
          >
          <div class="mt-1 flex rounded-md shadow-sm">
            <span
              class="inline-flex items-center rounded-l-md border border-r-0 border-gray-300 bg-gray-50 px-3 text-sm text-gray-500"
            >
              <icon name="ph:linkedin-logo-duotone" class="w-5 h-5" />
            </span>
            <input
              type="search"
              name="linkedin"
              id="linkedin"
              :value="linkedin"
              @input="$emit('update:linkedin', $event.target.value)"
              class="block w-full flex-1 rounded-none rounded-r-md border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm"
              placeholder="https://linkedin.com/elonmusk"
            />
          </div>
        </div>
        <div>
          <label for="instagram" class="block text-sm font-medium text-gray-700"
            >Email</label
          >
          <div class="mt-1 flex rounded-md shadow-sm">
            <span
              class="inline-flex items-center rounded-l-md border border-r-0 border-gray-300 bg-gray-50 px-3 text-sm text-gray-500"
            >
              <icon name="ph:envelope-duotone" class="w-5 h-5" />
            </span>
            <input
              type="search"
              name="email"
              id="email"
              :value="email"
              @input="$emit('update:email', $event.target.value)"
              class="block w-full flex-1 rounded-none rounded-r-md border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm"
              placeholder="elonmusk@geemail.com"
            />
          </div>
        </div>
        <div>
          <label for="instagram" class="block text-sm font-medium text-gray-700"
            >Youtube</label
          >
          <div class="mt-1 flex rounded-md shadow-sm">
            <span
              class="inline-flex items-center rounded-l-md border border-r-0 border-gray-300 bg-gray-50 px-3 text-sm text-gray-500"
            >
              <icon name="ph:youtube-logo-duotone" class="w-5 h-5" />
            </span>
            <input
              type="search"
              name="youtube"
              id="youtube"
              :value="youtube"
              @input="$emit('update:youtube', $event.target.value)"
              class="block w-full flex-1 rounded-none rounded-r-md border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm"
              placeholder="https://youtube.com/elonmusk"
            />
          </div>
        </div>
        <div>
          <label for="instagram" class="block text-sm font-medium text-gray-700"
            >Whatsapp</label
          >
          <div class="mt-1 flex rounded-md shadow-sm">
            <span
              class="inline-flex items-center rounded-l-md border border-r-0 border-gray-300 bg-gray-50 px-3 text-sm text-gray-500"
            >
              <icon name="ph:whatsapp-logo-duotone" class="w-5 h-5" />
            </span>
            <input
              type="text"
              name="whatsapp"
              id="whatsapp"
              :value="formattedWhatsapp"
              @input="onWhatsappInput($event.target.value)"
              class="block w-full flex-1 rounded-none rounded-r-md border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 sm:text-sm"
              placeholder="+1-555-123-4567"
              maxlength="16"
            />
          </div>
        </div>
      </div>
    </div>
  </base-form-section>
</template>
<script setup>
const props = defineProps([
  "facebook",
  "twitter",
  "instagram",
  "linkedin",
  "github",
  "telegram",
  "whatsapp",
  "youtube",
  "email",
]);
import { computed } from 'vue';

function formatUSNumber(input) {
  // Remove all non-digit characters except +
  let digits = input.replace(/[^\d]/g, '');
  if (!digits.startsWith('1')) digits = '1' + digits.replace(/^1*/, '');
  digits = digits.slice(0, 11); // +1 and 10 digits
  let formatted = '+1';
  if (digits.length > 1) formatted += '-' + digits.slice(1, 4);
  if (digits.length > 4) formatted += '-' + digits.slice(4, 7);
  if (digits.length > 7) formatted += '-' + digits.slice(7, 11);
  return formatted;
}

const formattedWhatsapp = computed(() => formatUSNumber(props.whatsapp || ''));
const isValidUSNumber = computed(() => {
  const digits = (props.whatsapp || '').replace(/[^\d]/g, '');
  return digits.length === 11 && digits.startsWith('1');
});

function onWhatsappInput(val) {
  // Remove all non-digit characters except +
  let digits = val.replace(/[^\d]/g, '');
  if (!digits.startsWith('1')) digits = '1' + digits.replace(/^1*/, '');
  digits = digits.slice(0, 11);
  let formatted = '+1';
  if (digits.length > 1) formatted += '-' + digits.slice(1, 4);
  if (digits.length > 4) formatted += '-' + digits.slice(4, 7);
  if (digits.length > 7) formatted += '-' + digits.slice(7, 11);
  $emit('update:whatsapp', formatted.replace(/[^\d]/g, '').replace(/^1/, '+1-').replace(/(\d{3})(\d{3})(\d{4})/, '+1-$1-$2-$3'));
}
</script>
