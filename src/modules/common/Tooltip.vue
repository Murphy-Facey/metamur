<template>
  <div
    class="tooltip absolute bottom-full -translate-y-2 left-1/2 -translate-x-1/2 w-max h-[40px] flex items-center bg-black px-2 rounded-[5px]"
  >
    <slot />
  </div>
</template>

<style lang="scss" scoped>
.tooltip {
  &::before {
    content: "";
    position: absolute;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    border: 6px solid transparent;
    border-top-color: black;
  }
}
</style>
