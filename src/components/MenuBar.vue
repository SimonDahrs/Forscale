<script setup lang="ts">
import {ref} from "vue";
import IconDropdown from "@/components/icons/IconDropdown.vue";
import IconUp from "@/components/icons/IconUp.vue";

const menuItems = ref([
  {
    "text": "Products",
    "link": "#",
    "subitems": [
      {
        "text": "ProjectWork",
        "link": "#"
      },
      {
        "text": "ProjectSheet",
        "link": "#"
      },
      {
        "text": "PlanBoard",
        "link": "#"
      }
    ]
  },
  {
    "text": "Services",
    "link": "#"
  },
  {
    "text": "Support",
    "link": "#"
  },
  {
    "text": "Pricing",
    "link": "#"
  },
  {
    "text": "Contact",
    "link": "#"
  },
])

const activeIndex = ref(0)
const subMenuActive = ref(false)

const emit = defineEmits({
  expanded: Boolean
})

function toggleSubMenu(index) {
  activeIndex.value = index
  subMenuActive.value = !subMenuActive.value
  emit('expanded', subMenuActive.value)
}
</script>

<template>
  <div id="menu-container">
    <nav class="menu">
      <template v-for="(item, index) in menuItems" :key="index">
        <a href="#" v-if="'subitems' in item" @click="toggleSubMenu(index)" :class="{active: activeIndex === index && subMenuActive}">
          <IconDropdown class="icon-dd" v-if="!subMenuActive"/>
          <IconUp v-else class="icon-dd" />
          {{item.text}}
        </a>
        <a href="#" v-else>{{item.text}}</a>
      </template>
    </nav>
    <nav class="submenu" :class="{active: subMenuActive}">
      <template v-for="(item, index) in menuItems[activeIndex].subitems" :key="index">
        <a href="#" v-if="'subitems' in item" @click="activeIndex = index">V {{item.text}}</a>
        <a href="#" v-else>{{item.text}}</a>
      </template>
    </nav>
  </div>
</template>

<style scoped>
.icon-dd {
  height: 16px;
  position: relative;
  top: 3px;
}
.menu {
  font-family: Inter;
  display: flex;
  flex-wrap: wrap;
  text-transform: uppercase;
  column-gap:  2rem;
  align-items: center;
  height: 64px;
}
.menu a{
  font-weight: 600;
  color: rgb(var(--fsblue-500));
  display: block;
  position: relative;
  &::before {
    content: "";
    position: absolute;
    width: 100%;
    height: 3px;
    bottom: -10px;
    left: 0px;
    background-color: rgb(var(--fsblue-100));
    transition: all 0.2s ease-in-out;
    transform: scale(0, 0);
    visibility: hidden;
  }
}

.menu a:hover {
  color: rgb(var(--fsblue-200));
  &::before {
    visibility: visible;
    transform: scale(1, 1);
  }
}

.menu a.active {
  color: rgb(var(--fsblue-200));
}

.submenu {
  display: flex;
  column-gap: 2rem;
  transform: scaleY(0);
  transition: transform 100ms linear;
  transform-origin: top;
}

.submenu.active {
  transform: scaleY(1);
}


.submenu a {
  color: rgb(var(--fsblue-400));
}

.submenu a:hover{
  text-decoration: underline;
}
</style>