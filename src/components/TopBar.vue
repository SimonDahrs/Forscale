<script setup lang="ts">

import MenuBar from "@/components/MenuBar.vue";
import {ref} from "vue";

const expanded = ref(false)

function handleExpanded(value: boolean) {
  expanded.value = value;
}
</script>

<template>
  <div id="top-bar" :class="{expanded: expanded}">
    <img src="@/assets/logo.png" id="logo"/>
    <MenuBar @expanded="handleExpanded"/>
  </div>
</template>

<style scoped>
#top-bar {
  overflow-anchor: none;
  width: 100%;
  max-width: var(--max-width);
  padding: .3rem 0 .3rem 0;
  display: flex;
  justify-content: space-between;
  margin: 0 auto;
  height: calc(64px + .6rem);
  transition: height 0.3s ease;
}

#top-bar.expanded {
  height: 128px;

}

#logo {
  height: 64px;
}
</style>