<template>
  <button @click="generateWord" class="download-button">
    <div class="docs">
      <svg viewBox="0 0 24 24" width="20" height="20" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round" class="css-i6dzq1">
        <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path>
        <polyline points="14 2 14 8 20 8"></polyline>
        <line x1="16" y1="13" x2="8" y2="13"></line>
        <line x1="16" y1="17" x2="8" y2="17"></line>
        <polyline points="10 9 9 9 8 9"></polyline>
      </svg>
      DOCS
    </div>
    <div class="download">
      <svg viewBox="0 0 24 24" width="24" height="24" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round" class="css-i6dzq1">
        <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
        <polyline points="7 10 12 15 17 10"></polyline>
        <line x1="12" y1="15" x2="12" y2="3"></line>
      </svg>
    </div>
  </button>
</template>

<script>
import PizZip from "pizzip";
import Docxtemplater from "docxtemplater";
import { saveAs } from "file-saver";
import { ref } from "vue";

export default {
  props: ["data"],
  methods: {
    async generateWord() {
      // Fetch the template DOCX file
      const response = await fetch('/template.docx');
      const arrayBuffer = await response.arrayBuffer();

      // Load the template into PizZip
      const zip = new PizZip(arrayBuffer);
      const doc = new Docxtemplater(zip);

      // Set the data for the placeholders
      doc.setData(this.data);

      try {
        // Render the document
        doc.render();
        // Generate the Word file and save it
        const blob = doc.getZip().generate({ type: "blob" });
        saveAs(blob, "cv.docx");
      } catch (error) {
        console.error("Error generating Word document: ", error);
      }
    }
  }
};
</script>
