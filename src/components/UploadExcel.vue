<template>
    <div>
        <h1>Upload Excel File</h1>
        <input type="file" @change="handleFileUpload" />
        <button @click="processFile">Process File</button>
  </div>
</template>
<script>
import * as XLSX from "xlsx";

export default {
    name: 'UploadExcel',
  data() {
    return {
      file: null,
      jsonData: null,
    };
  },
  methods: {
    handleFileUpload(event) {
      this.file = event.target.files[0];
    },
    processFile() {
      if (!this.file) {
        alert("Please select a file.");
        return;
      }

      const reader = new FileReader();
      reader.onload = (e) => {
        const data = new Uint8Array(e.target.result);
        const workbook = XLSX.read(data, { type: "array" });
        const firstSheetName = workbook.SheetNames[0];
        const worksheet = workbook.Sheets[firstSheetName];
        this.jsonData = XLSX.utils.sheet_to_json(worksheet);

        // Log the data to the console
        console.log(this.jsonData);
      };
      reader.readAsArrayBuffer(this.file);
    },
  },
};
</script>
<style></style>