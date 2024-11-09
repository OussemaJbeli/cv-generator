<template>
  <div class="app">
    <div class="first_part">
      <CvForm @form-submitted="setCvData" />
    </div>
    <div class="second_part">
      <CvTemplate v-if="cvData" :data="cvData" />
      <div class="download_buttons">
        <PdfExport v-if="cvData" :data="cvData" />
        <WordExport v-if="cvData" :data="cvData" />
      </div>
    </div>
  </div>
</template>
<script>
import CvForm from "./components/CvForm.vue";
import CvTemplate from "./components/CvTemplate.vue";
import PdfExport from "./components/PdfExport.vue";
import WordExport from "./components/WordExport.vue";

export default {
  components: {
    CvTemplate,
    CvForm,
    PdfExport,
    WordExport,
  },
  data() {
    return {
      cvData: null,  // Ensure cvData is initialized to null
    };
  },
  methods: {
    setCvData(data) {
      this.cvData = data;  // Set cvData when form is submitted
    }
  }
}
</script>

