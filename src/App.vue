<template>
  <div id="app">
    <div class="first_part">
      <CvForm @form-submitted="setCvData" />
    </div>
    <div class="second_part">
      <CvTemplate v-if="cvData" :data="cvData" />
      <PdfExport v-if="cvData" :data="cvData" />
      <WordExport v-if="cvData" :data="cvData" />
    </div>
  </div>
</template>

<script>
import CvForm from "./components/CvForm.vue";
import CvTemplate from "./components/CvTemplate.vue";
import PdfExport from "./components/PdfExport.vue";
import WordExport from "./components/WordExport.vue";

export default {
  components: { CvForm, CvTemplate, PdfExport, WordExport },
  data() {
    return {
      cvData: null
    };
  },
  methods: {
    setCvData(data) {
      this.cvData = data;
    }
  }
};
</script>
