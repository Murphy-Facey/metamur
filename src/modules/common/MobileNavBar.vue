<script lang="ts" setup>
import { ref } from "vue";
import IconBars from "@/modules/icons/IconBars.vue";
import IconFile from "../icons/IconFile.vue";

const menuItems = [
  { name: "home", displayName: "Home" },
  { name: "about", displayName: "About Me" },
  { name: "projects", displayName: "Projects/Work" },
  { name: "contact", displayName: "Contact" },
];

const selectedMenuItem = ref("home");
const isMenuShowing = ref(false);

const changeMenuItem = (menuItemName: string) => {
  selectedMenuItem.value = menuItemName;
};

const toggleMenuShowing = () => {
  isMenuShowing.value = !isMenuShowing.value;
};
</script>

<template>
  <button
    class="relative ml-auto p-2 border border-neutral-600 rounded-[5px]"
    @click.stop="toggleMenuShowing"
  >
    <icon-bars class="fill-white w-4" />
    <nav
      v-if="isMenuShowing"
      class="absolute top-full translate-y-2 right-0 w-[200px] bg-neutral-900 py-2 text-left border border-neutral-600 rounded-[5px]"
    >
      <div class="nav_tooltip relative text-neutral-600 font-semibold">
        <p
          v-for="(item, index) in menuItems"
          :key="`mobile-menu-item-${index}`"
          :class="{ active: item.name === selectedMenuItem }"
          @click="changeMenuItem(item.name)"
        >
          {{ item.displayName }}
        </p>
      </div>
      <button
        class="group flex items-center gap-x-2 mt-3 ml-3 p-2 border border-neutral-700 hover:border-neutral-400 text-neutral-400 text-sm font-medium rounded-[5px]"
      >
        <IconFile
          class="fill-neutral-700 group-hover:fill-neutral-400 w-3 pb-0.5"
        />
        Download Resume
      </button>
    </nav>
  </button>
</template>

<style lang="scss" scoped>
.nav_tooltip {
  &::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 10px;
    transform: translateY(-50%);
    height: 100%;
    width: 1px;

    @apply bg-neutral-600;
  }

  p {
    padding-left: 20px;
    position: relative;
    &:hover,
    &.active {
      //   background-color: gray;
      font-weight: 600;
      @apply bg-neutral-700 text-white;
      &::before {
        @apply bg-white;
      }
    }

    &::before {
      content: "";
      position: absolute;
      top: 0;
      left: 10px;
      width: 1px;
      height: 100%;
    }
  }
}
</style>
