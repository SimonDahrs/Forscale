<script setup lang="ts"></script>

<template>
  <div id="banner">
    <div id="bg-image"></div>
    <div id="text-container">
      <span class="banner header">Successful projects start with good planning.</span>
      <span class="banner subheader">Good planning starts with Forscale.</span>
      <div id="action-buttons">
        <a class="action-button blue" href="#"
          >Try ProjectWork For Free <span class="bold">→</span></a
        >
        <a class="action-button white" href="#">Learn More <span class="bold">→</span></a>
      </div>
    </div>
  </div>
</template>

<style scoped>
#action-buttons {
  display: flex;
  flex-direction: row;
  gap: 1rem;
  margin-top: 1rem;
}

#banner {
  width: 100%;
  height: 500px;
  position: relative;
}

.banner {
  font-family: Inter;
  text-transform: capitalize;
  color: white;
  font-weight: bold;
  max-width: 640px;
  display: block;
}

.banner.header {
  font-size: 4rem;
}

.banner.subheader {
  font-size: 2rem;
}

#bg-image {
  background-image: url('@/assets/banner.jpg'),
    linear-gradient(90deg, rgba(var(--fsblue-500), 0.8), rgba(var(--fsblue-500), 0.3) 70%);
  background-blend-mode: overlay;
  background-size: cover;
  background-attachment: fixed;
  background-position: 0% 80%;
  width: 100%;
  height: 100%;
  filter: saturate(30%);
}

#text-container {
  position: absolute;
  top: 0;
  max-width: var(--max-width);
  margin: 0 auto;
  left: 0;
  right: 0;
  padding: 1.5rem 0 1.5rem 0;
}
</style>
