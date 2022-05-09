<script lang="ts" setup>
import { ref } from "vue";
import IconFile from "@/modules/icons/IconFile.vue";
import MobileNavBar from "./MobileNavBar.vue";

const menuItems = [
  { name: "home", displayName: "Home" },
  { name: "about", displayName: "About Me" },
  { name: "projects", displayName: "Projects/Work" },
  { name: "contact", displayName: "Contact" },
];

const selectedMenuItem = ref("home");

const changeMenuItem = (menuItemName: string) => {
  selectedMenuItem.value = menuItemName;
};
</script>

<template>
  <header class="w-full max-w-[1200px] h-[64px] flex items-center">
    <div class="flex items-center gap-x-4">
      <img src="@/assets/logo.svg" alt="logo" class="w-12" />
      <h2 class="text-2xl text-neutral-500 font-fancy">Murphy D. Facey</h2>
    </div>
    <nav class="hidden lg:flex ml-auto items-center">
      <ul class="flex gap-x-3">
        <li
          v-for="(item, index) in menuItems"
          :key="`menu-items-${index}`"
          class="menu_items px-2 pt-1 pb-1.5 font-medium rounded-[5px] select-none"
          :class="{
            active: item.name === selectedMenuItem,
          }"
          @click="changeMenuItem(item.name)"
        >
          {{ item.displayName }}
        </li>
      </ul>
      <button
        class="group flex items-center gap-x-2 ml-3 p-2 border border-neutral-700 hover:border-neutral-400 text-neutral-400 text-sm font-medium rounded-[5px]"
      >
        <icon-file
          class="fill-neutral-700 group-hover:fill-neutral-400 w-3 pb-0.5"
        />
        Download Resume
      </button>
    </nav>

    <mobile-nav-bar class="block lg:hidden" />
  </header>
</template>

<style lang="scss" scoped>
$border-offset: 10%;

.menu_items {
  position: relative;
  transition: color linear 250ms;
  @apply text-neutral-600;

  &::before {
    content: "";
    position: absolute;
    bottom: 4px;
    left: $border-offset;
    width: 0px;
    height: 4px;
    border-radius: 5px;

    @apply bg-sky-500;
  }

  &:hover {
    cursor: pointer;

    @apply bg-neutral-700 text-neutral-300;

    &::before {
      animation: animate-border 250ms forwards;
    }
  }

  &.active {
    @apply bg-neutral-600 text-neutral-300;
  }
}

@keyframes animate-border {
  0% {
    width: 0;
  }

  100% {
    width: calc(100% - ($border-offset * 2));
  }
}
</style>
