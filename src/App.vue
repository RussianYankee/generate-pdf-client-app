<template>
  <div class="pdf-form">
    <input type="text" name="name" placeholder="Customer's name" v-model="formData.name"/>
    <input type="number" name="receiptID" placeholder="Receipt ID" v-model="formData.receiptID"/>
    <input type="number" name="price1" placeholder="Price 1" v-model="formData.price1"/>
    <input type="number" name="price2" placeholder="Price 2" v-model="formData.price2"/>
    <button @click="createAndDownloadPdf">Create & Download PDF</button>
  </div>
</template>

<script setup lang="ts">
import axios from 'axios';
import { ref } from 'vue'
//import { saveAs } from 'file-saver';

const formData = ref({
  name: "",
  receiptID: 123,
  price1: 333.44,
  price2: 149.99
})

function createAndDownloadPdf() {
  axios.post('/create-pdf', formData)
}
</script>

<style scoped>
#app{
  height: 100%;
}
.pdf-form{
  display: flex;
  flex-direction: column;
  min-width: 450px;
  flex-wrap: wrap;
  align-items: center;
  align-content: center;
}
</style>
