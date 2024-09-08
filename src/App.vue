<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import TopBar from '@/components/TopBar.vue'
import HomeView from '@/views/HomeView.vue'
</script>

<template>
  <header>
    <TopBar />
  </header>

  <HomeView />
</template>

<style scoped>
header {
  position: sticky;
  top: 0;
  z-index: 1;
  background-color: var(--color-background);
}
</style>
