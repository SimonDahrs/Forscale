<script setup lang="ts">
import HomeBanner from '@/components/HomeBanner.vue'
import SellingPoints from '@/components/SellingPoints.vue'
import AboutSection from '@/components/AboutSection.vue'
</script>

<template>
  <main>
    <HomeBanner id="banner" />
    <div class="section">
      <div class="content">
        <h1>ABOUT US</h1>
        <AboutSection />
      </div>
    </div>
    <div class="section blue">
      <h1 style="text-align: center">PRODUCTS</h1>
      <div class="content">
        <SellingPoints />
      </div>
    </div>
  </main>
</template>
<style scoped>
h1 {
  padding: 0 0 1.5rem 0;
}

#banner {
  //z-index: -1;
  //position: fixed;
  //top: 0;
}
</style>
