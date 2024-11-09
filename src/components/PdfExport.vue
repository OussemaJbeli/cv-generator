<!-- src/components/PdfExport.vue -->
<template>
  <button  @click="generatePDF" class="download-button">
      <div class="docs">
        <svg
          viewBox="0 0 24 24"
          width="20"
          height="20"
          stroke="currentColor"
          stroke-width="2"
          fill="none"
          stroke-linecap="round"
          stroke-linejoin="round"
          class="css-i6dzq1"
        >
          <path
            d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"
          ></path>
          <polyline points="14 2 14 8 20 8"></polyline>
          <line x1="16" y1="13" x2="8" y2="13"></line>
          <line x1="16" y1="17" x2="8" y2="17"></line>
          <polyline points="10 9 9 9 8 9"></polyline>
        </svg>
        PDF
      </div>
      <div class="download">
        <svg
          viewBox="0 0 24 24"
          width="24"
          height="24"
          stroke="currentColor"
          stroke-width="2"
          fill="none"
          stroke-linecap="round"
          stroke-linejoin="round"
          class="css-i6dzq1"
        >
          <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
          <polyline points="7 10 12 15 17 10"></polyline>
          <line x1="12" y1="15" x2="12" y2="3"></line>
        </svg>
      </div>
  </button>
</template>
  
<script>
  import jsPDF from "jspdf";
  import html2canvas from "html2canvas";
  
  export default {
    props: ["data"],
    methods: {
  async generatePDF() {
    // Wait for the DOM to update and capture the CV content
    this.$nextTick(async () => {
      const cvElement = document.getElementById("cv-template");

      if (!cvElement) {
        console.error("CV template element not found!");
        return;
      }

      const canvas = await html2canvas(cvElement);
      const imgData = canvas.toDataURL("image/png");

      // Create a new jsPDF instance
      const pdf = new jsPDF();
      
      // Get the dimensions of the PDF page (A4 size by default)
      const pdfWidth = pdf.internal.pageSize.width;
      const pdfHeight = pdf.internal.pageSize.height;

      // Get the canvas width and height
      const canvasWidth = canvas.width;
      const canvasHeight = canvas.height;

      // Calculate the scale factor to fit the canvas to the PDF
      const scaleX = pdfWidth / canvasWidth;
      const scaleY = pdfHeight / canvasHeight;

      // Use the smaller scale to ensure the content fits within the page
      const scale = Math.min(scaleX, scaleY);

      // Add the image to the PDF with the scaled dimensions
      pdf.addImage(imgData, "PNG", 0, 0, canvasWidth * scale, canvasHeight * scale);

      // Save the PDF
      pdf.save("cv.pdf");
    });
  }
}

  };
</script>
  