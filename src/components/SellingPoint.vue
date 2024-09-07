<script setup lang="ts">
defineProps({
  data: Object,
  variant: Number
})
</script>

<template>
  <RouterLink :to="data.link" class="sp">
    <div>
      <p class="sp-text sp-title">{{ data.title }}</p>
      <p class="sp-text">{{ data.text }}</p>
    </div>
  </RouterLink>
</template>

<style scoped>
.sp {
  display: inline-block;
  background-color: rgb(var(--fsblue-500));
  color: white;
  box-shadow: rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px 3px 6px;
  transition: all 0.3s cubic-bezier(.25, .8, .25, 1);
  padding: 1rem;
  text-align: center;
  border-radius: var(--border-radius);
  transition: all 0.2s ease-in-out;
}

.sp:hover {
  transform: scale(1.05);
}

.sp:nth-child(2) {
  background-color: rgb(var(--fsblue-100));
  color: black;
}

.sp:nth-child(3) {
  background-color: rgb(var(--fsblue-300));
}

.sp-title {
  font-family: Inter;
  font-weight: bold;
  font-size: 2rem;
}
</style>