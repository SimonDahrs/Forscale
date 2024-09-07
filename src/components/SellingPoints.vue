<script setup lang="ts">
import {ref} from "vue";
import SellingPoint from "@/components/SellingPoint.vue";

const products = ref([
  {
    "title": "ProjectWork",
    "text": "Powerful, user-friendly online projectmanagement",
    "link": "#"
  },
  {
    "title": "ProjectSheet",
    "text": "Projectmanagement via Google Sheets integration",
    "link": "#"
  }
  ,
  {
    "title": "PlanBoard",
    "text": "Planning using Google Calendar",
    "link": "#"
  }
])
</script>

<template>
  <div id="sp-container">
    <SellingPoint v-for="(product, index) in products" :key="index" :data="product" :variant="index % 2"/>
  </div>
</template>

<style scoped>
#sp-container {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 2rem;
  justify-content: center;
  justify-items: center;
  max-width: 800px;
  margin: 0 auto;
}

@media only screen and (max-width: 768px) {
  #sp-container {
    grid-template-columns: auto;
  }
}
</style>