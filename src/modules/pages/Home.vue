<script lang="ts" setup>
import Tooltip from "@/modules/common/Tooltip.vue";
import Editor from "../common/Editor.vue";
</script>

<template>
  <section
    class="relative w-full max-w-[1200px] h-[calc(100vh-100px)] flex items-center mt-[36px] bg-neutral-700"
  >
    <div class="ml-[50px]">
      <h3 class="flex items-end text-2xl text-neutral-800 uppercase font-black">
        <img
          src="@/assets/images/hand-wave.gif"
          alt="wave"
          class="w-8 select-none"
        />
        Hey there, I am
      </h3>
      <h1 class="text-4xl text-neutral-400 uppercase">Murphy D. Facey</h1>
      <p class="w-full max-w-[500px] mt-4 text-neutral-400">
        I am
        <span
          class="px-1 py-0.5 text-neutral-600 font-medium line-through bg-neutral-800 rounded-[3px]"
          >a software</span
        >
        currently front-end developer based in the beautiful island Jamaica. Are
        you interested in creating beautiful website using these
        <span
          class="group relative inline hover:text-neutral-200 border-b-2 border-dashed border-neutral-400 hover:cursor-pointer"
        >
          <tooltip class="hidden group-hover:flex">
            <div class="h-[60%] flex gap-x-2">
              <img src="@/assets/images/vite-logo.svg" alt="nuxt" />
              <img src="@/assets/images/vue-logo.png" alt="nuxt" />
              <img src="@/assets/images/sass-logo.png" alt="nuxt" />
              <img src="@/assets/images/tailwind-logo.png" alt="nuxt" />
            </div>
          </tooltip>
          technologies </span
        >? Are you interested in tutoring?
      </p>
      <div class="mt-[50px]">
        <button class="bg-neutral-500 mr-4 px-4 py-3 font-medium rounded-[5px]">
          Contact me
        </button>
        <button
          class="px-4 py-3 text-neutral-500 font-medium border-2 border-neutral-600 rounded-[5px]"
        >
          View Project
        </button>
      </div>
    </div>
    <img
      src="@/assets/images/blob.svg"
      alt="blob"
      class="absolute top-1/2 -translate-y-1/2 right-0"
    />
    <div
      class="absolute top-1/2 -translate-y-1/2 right-[100px] flex flex-col gap-y-10"
    >
      <Editor />
      <Editor />
      <Editor />
    </div>
  </section>
</template>
