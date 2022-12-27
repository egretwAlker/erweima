<script>
import './index.css';
import QrcodeVue from 'qrcode.vue';
import {QrStream, QrCapture, QrDropzone} from 'vue3-qr-reader';

export default {
  data() {
    return {
      message: "https://google.com",
      fc: 0
    }
  },
  methods: {
    onDecode(s) {
      this.message = s;
    }
  },
  components: {
    QrcodeVue,
    QrStream,
    QrCapture,
    QrDropzone
  },
};
</script>

<template>
<div class="flex-row items-center mx-auto w-full lg:max-w-md min-h-screen bg-white shadow">
<input class="rounded-lg bg-gray-500 w-full" type="text" v-model="message" />
<div @click="fc = 1-fc">
<QrcodeVue v-if="fc === 0" :value="message" :size="300" class="mx-auto"></QrcodeVue>
<QrStream v-else @decode="onDecode" class="w-full"/>
</div>
</div>
</template>