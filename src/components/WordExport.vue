<!-- src/components/WordExport.vue -->
<template>
    <button @click="generateWord">Download Word</button>
  </template>
  
  <script>
  import PizZip from "pizzip";
  import Docxtemplater from "docxtemplater";
  import { saveAs } from "file-saver";
  
  export default {
    props: ["data"],
    methods: {
      generateWord() {
        const zip = new PizZip();
        const doc = new Docxtemplater(zip);
  
        doc.setData(this.data);
  
        try {
          doc.render();
          const blob = doc.getZip().generate({ type: "blob" });
          saveAs(blob, "cv.docx");
        } catch (error) {
          console.error(error);
        }
      }
    }
  };
  </script>
  