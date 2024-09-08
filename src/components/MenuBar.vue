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

const hbmenuOpened = ref(false)

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
    <div id="std-menu">
      <nav class="menu">
        <template v-for="(item, index) in menuItems" :key="index">
          <a class="menu-item-top" href="#" v-if="'subitems' in item" @click="toggleSubMenu(index)"
             :class="{active: activeIndex === index && subMenuActive}">
            <IconDropdown class="icon-dd" v-if="!subMenuActive"/>
            <IconUp v-else class="icon-dd"/>
            {{ item.text }}
          </a>
          <a class="menu-item-top" href="#" v-else>{{ item.text }}</a>
        </template>
      </nav>
      <nav class="submenu" :class="{active: subMenuActive}">
        <template v-for="(item, index) in menuItems[activeIndex].subitems" :key="index">
          <a class="menu-item-sub" href="#">{{ item.text }}</a>
        </template>
      </nav>
    </div>
    <div id="hamburger-menu">
      <div id="hamburger-toggle" @click="hbmenuOpened = !hbmenuOpened" :class="{ opened: hbmenuOpened }">
        <span class="button-icon" :class="{ opened: hbmenuOpened }" id="openMenu">☰</span>
        <span class="button-icon" :class="{ opened: hbmenuOpened }" id="closeMenu">✕</span>
      </div>
      <div id="hamburger-menu-item-container" :class="{ opened: hbmenuOpened }">
        <a v-for="(item, index) in menuItems" :key="index" class="menu-item-sub" href="{{item.link}}">{{
            item.text
          }}</a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.icon-dd {
  height: 16px;
  position: relative;
  top: 3px;
}

.menu {
  font-family: Inter, sans-serif;
  display: flex;
  flex-wrap: wrap;
  text-transform: uppercase;
  column-gap: 2rem;
  align-items: center;
  height: 64px;
}

.menu-item-top {
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

.menu-item-top:hover {
  color: rgb(var(--fsblue-200));

  &::before {
    visibility: visible;
    transform: scale(1, 1);
  }
}

.menu-item-top.active {
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


.menu-item-sub {
  color: rgb(var(--fsblue-400));
}

.menu-item-sub:hover {
  text-decoration: underline;
}

#openMenu {
  opacity: 1;
  transition: transform .2s ease-in-out;
  transform: scale(1) rotate(0);
}

#openMenu.opened {
  transform: scale(0) rotate(90deg);
}

#closeMenu {
  transition: transform .2s ease-in-out;
  transform: scale(0) rotate(-90deg);
}

.button-icon {
  position: absolute;
  width: 50px;
  text-align: center;
}

#closeMenu.opened {
  opacity: 1;
  transform: scale(1) rotate(0);
}

#hamburger-menu {
  display: none;
  position: fixed;
  top: .5rem;
  right: .5rem;
  z-index: 5;
  display: none;
  row-gap: .5rem;
}

#hamburger-menu ul {
  list-style-type: none;
  padding: 0;
}

#hamburger-toggle {
  font-weight: bold;
  font-size: 24px;
  box-sizing: border-box;
  background: rgba(var(--fsblue-300), 0.5);
  border-radius: 50%;
  display: flex;
  justify-content: center;
  height: 50px;
  width: 50px;
  text-align: center;
  align-items: center;
  cursor: pointer;
  transition: transform .3s ease-out;
  box-shadow: 0.1px 0.1px 0.3px rgba(0, 0, 0, 0.02),
  0.1px 0.1px 0.8px rgba(0, 0, 0, 0.028),
  0.3px 0.3px 1.5px rgba(0, 0, 0, 0.035),
  0.4px 0.4px 2.7px rgba(0, 0, 0, 0.042),
  0.8px 0.8px 5px rgba(0, 0, 0, 0.05),
  2px 2px 12px rgba(0, 0, 0, 0.07);
}

#hamburger-toggle:hover {
  background: rgb(var(--fsblue-300));
  color: white;
  transform: scale(1.1);
  box-shadow: 0.4px 0.4px 0.3px rgba(0, 0, 0, 0.02),
  1px 1px 0.8px rgba(0, 0, 0, 0.028),
  1.9px 1.9px 1.5px rgba(0, 0, 0, 0.035),
  3.4px 3.4px 2.7px rgba(0, 0, 0, 0.042),
  6.3px 6.3px 5px rgba(0, 0, 0, 0.05),
  15px 15px 12px rgba(0, 0, 0, 0.07);
}

#hamburger-toggle.opened {
  background: rgb(var(--fsblue-500));
  color: white;
}

#hamburger-menu-item-container {
  font-size: 20px;
  transform: scaleY(0);
  background-color: var(--color-background);
  z-index: 5;
  box-shadow: 0 3px 10px rgb(0 1 1 / 0.3);
  border: 1px solid rgba(200, 200, 200, 0.3);
  border-radius: 7px;
  transition: transform .15s;
  transform-origin: top;
  padding: 1.5rem 2rem 1.5rem 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: .5rem;
}

#hamburger-menu-item-container.opened {
  transform: scaleY(1);
}

#hamburger-menu-item-container a {
  color: rgb(var(--fsblue-500));
}


@media only screen and (max-width: 768px) {
  #std-menu {
    display: none;
  }

  #hamburger-menu {
    display: grid;
    justify-items: end;
  }
}

</style>