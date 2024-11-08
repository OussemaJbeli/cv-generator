<!-- src/components/PdfExport.vue -->
<template>
    <button @click="generatePDF">Download PDF</button>
  </template>
  
  <script>
  import jsPDF from "jspdf";
  import html2canvas from "html2canvas";
  
  export default {
    props: ["data"],
    methods: {
      async generatePDF() {
        const cvElement = document.getElementById("cv-template");

        if (!cvElement) {
          console.error("CV template element not found!");
          return;
        }

        const canvas = await html2canvas(cvElement);
        const imgData = canvas.toDataURL("image/png");
        const pdf = new jsPDF();
        pdf.addImage(imgData, "PNG", 10, 10, 180, 160); // Adjust as needed
        pdf.save("cv.pdf");
      }
    }

  };
  </script>
  