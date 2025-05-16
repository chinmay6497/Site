<template>
  <div :class="['h-screen grid grid-cols-3 divide-x', colorMode.value === 'dark' ? 'dark bg-slate-900 text-white' : 'bg-white text-black']">
    <div class="col-span-2 h-screen flex flex-col bg-slate-100">
      <div class="flex-1 overflow-y-auto p-8">
        <button @click="showTemplateModal = true" class="mb-4 px-4 py-2 bg-blue-100 rounded text-blue-800 font-semibold">Change Template</button>
        <app-form-profile
          v-model:name="data.n"
          v-model:desc="data.d"
          v-model:image="data.i"
        />
        <app-form-hr />
        <app-form-social-links
          v-model:facebook="data.f"
          v-model:twitter="data.t"
          v-model:instagram="data.ig"
          v-model:github="data.gh"
          v-model:telegram="data.tg"
          v-model:linkedin="data.l"
          v-model:email="data.e"
          v-model:whatsapp="data.w"
          v-model:youtube="data.y"
        />
        <app-form-hr />
        <app-form-links v-model="data.ls" />
      </div>
      <div class="border-t bg-white flex items-center">
        <button
          @click="prefillDemoData"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Add demo data </span>
          <icon name="mdi:code-json" class="h-4 w-4" />
        </button>
        <button
          @click="publish"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Publish </span>
          <icon name="ph:paper-plane-tilt-bold" class="h-4 w-4" />
        </button>
        <button
          @click="publishWithQR"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Publish with QR Code </span>
          <icon name="mdi:qrcode" class="h-4 w-4" />
        </button>
        <a
          href="https://github.com/chinmay6497"
          target="_blank"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Made with love by Chinmay Raval </span>
          <icon name="mdi:github" class="h-4 w-4" />
        </a>
      </div>
    </div>
    <app-form-preview :data="data" :templateName="selectedTemplate" />

    <div v-if="showTemplateModal" class="fixed inset-0 bg-black bg-opacity-40 flex items-center justify-center z-50">
      <div class="bg-white rounded-lg shadow-lg p-6 w-[400px] max-w-full relative">
        <button @click="showTemplateModal = false" class="absolute top-2 right-2 text-gray-400 hover:text-gray-700">✕</button>
        <h3 class="text-lg font-bold mb-4">Select a Template</h3>
        <div class="grid grid-cols-2 gap-4">
          <div v-for="tpl in templates" :key="tpl.name" @click="selectTemplate(tpl.component)" :class="['cursor-pointer border rounded-lg p-2 flex flex-col items-center', selectedTemplate === tpl.component ? 'border-blue-500 ring-2 ring-blue-200' : 'border-gray-200']">
            <img :src="tpl.thumbnail" :alt="tpl.name" class="w-24 h-16 object-cover rounded mb-2" />
            <span class="font-medium">{{ tpl.name }}</span>
          </div>
        </div>
      </div>
    </div>

    <div v-if="showQRModal" class="fixed inset-0 bg-black bg-opacity-40 flex items-center justify-center z-50">
      <div class="bg-white rounded-lg shadow-lg p-6 w-[400px] max-w-full relative flex flex-col items-center">
        <button @click="showQRModal = false" class="absolute top-2 right-2 text-gray-400 hover:text-gray-700">✕</button>
        <h3 class="text-lg font-bold mb-4">Your QR Code</h3>
        <img :src="qrCodeDataUrl" alt="QR Code" class="mb-4 w-48 h-48" />
        <button @click="downloadQR" class="px-4 py-2 bg-blue-600 text-white rounded font-semibold">Download QR Code</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { encodeData } from "../utils/transformer";
import { ref } from 'vue';
import templatesMeta from '../components/Templates/templates.json';
import QRCode from 'qrcode';

const colorMode = useColorMode();

const data = ref({
  n: "John Snow",
  d: "I'm John Snow, the king in the north. I know Nothing.",
  i: "https://i.insider.com/56743fad72f2c12a008b6cc0",
  f: "https://www.facebook.com/john_snow",
  t: "https://twitter.com/john_snow",
  ig: "https://www.instagram.com/john_snow",
  e: "mail@john_snow.cc",
  gh: "https://github.com/john_snow",
  tg: "https://t.me/john_snow",
  w: "+918888888888",
  y: "https://youtube.com/@john_snow",
  l: "https://linkedin.com/john_snow",
  ls: [
    {
      l: "My Website",
      i: "ph:globe-duotone",
      u: "https://example.com",
    },
    {
      l: "Amazon wishlist",
      i: "ant-design:amazon-outlined",
      u: "https://amazon.in",
    },
    {
      l: "React JS course",
      i: "grommet-icons:reactjs",
      u: "https://reactjs.org/",
    },
    {
      l: "Donate for our cause",
      i: "iconoir:donate",
      u: "https://who.int",
    },
    {
      l: "Download my resume",
      i: "ph:file-pdf",
      u: "https://google.com",
    },
  ],
});

const showTemplateModal = ref(false);
const selectedTemplate = ref('Minimal');
const templates = templatesMeta;
const showQRModal = ref(false);
const qrCodeDataUrl = ref('');

function selectTemplate(name) {
  selectedTemplate.value = name;
  showTemplateModal.value = false;
}

const prefillDemoData = () => {
  data.value = {
    n: "John Snow",
    d: "I'm John Snow, the king in the north. I know Nothing.",
    i: "https://i.insider.com/56743fad72f2c12a008b6cc0",
    f: "https://www.facebook.com/john_snow",
    t: "https://twitter.com/john_snow",
    ig: "https://www.instagram.com/john_snow",
    e: "mail@john_snow.cc",
    gh: "https://github.com/john_snow",
    tg: "https://t.me/john_snow",
    w: "+918888888888",
    y: "https://youtube.com/@john_snow",
    l: "https://linkedin.com/john_snow",
    ls: [
      {
        l: "My Website",
        i: "ph:globe-duotone",
        u: "https://example.com",
      },
      {
        l: "Amazon wishlist",
        i: "ant-design:amazon-outlined",
        u: "https://amazon.in",
      },
      {
        l: "React JS course",
        i: "grommet-icons:reactjs",
        u: "https://reactjs.org/",
      },
      {
        l: "Donate for our cause",
        i: "iconoir:donate",
        u: "https://who.int",
      },
      {
        l: "Download my resume",
        i: "ph:file-pdf",
        u: "https://google.com",
      },
    ],
  };
};

const publish = () => {
  const url = `${window.location.origin}/1?data=${encodeData(data.value)}`;
  navigator.clipboard.writeText(url).then(() => {
    alert("Link copied to clipboard");
  });
};

async function publishWithQR() {
  const url = `${window.location.origin}/1?data=${encodeData(data.value)}`;
  qrCodeDataUrl.value = await QRCode.toDataURL(url, { width: 300 });
  showQRModal.value = true;
  navigator.clipboard.writeText(url);
}

function downloadQR() {
  const a = document.createElement('a');
  a.href = qrCodeDataUrl.value;
  a.download = 'onelink-qr.png';
  a.click();
}
</script>
