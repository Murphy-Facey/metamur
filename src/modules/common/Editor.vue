<script lang="ts" setup>
// import Prism Editor
import { onMounted, ref } from "vue";
import { PrismEditor } from "vue-prism-editor";
import "vue-prism-editor/dist/prismeditor.min.css"; // import the styles somewhere

// import highlighting library (you can use any library you want just return html string)
import { highlight, languages } from "prismjs/components/prism-core";
import "prismjs/components/prism-clike";
import "prismjs/components/prism-javascript";
import "prism-themes/themes/prism-material-dark.css"; // import syntax highlighting styles

const code =
  ref(`/** this is a simple comment to let you know that I am a boss **/
const foo = (bar) => {
  var a = 42,
      b = 'Prism';
  return a + bar(b);
}`);

const codeSnippet = ref("");
const i = ref(0);
const timer = ref(-1);

onMounted(() => {
  timer.value = setInterval(() => {
    if (i.value === code.value.length) {
      clearInterval(timer.value);
      return;
    }
    codeSnippet.value += code.value.charAt(i.value);
    i.value += 1;
  }, 200);
});

const highlighter = (code: string) => {
  return highlight(code, languages.js);
};
</script>

<template>
  <section
    class="w-[500px] bg-neutral-800/60 backdrop-blur p-[10px] rounded-[5px] shadow-lg"
  >
    <div>css</div>
    <prism-editor
      class="editor text-white text-sm"
      v-model="codeSnippet"
      :highlight="highlighter"
      line-numbers
      readonly
    ></prism-editor>
  </section>
</template>

<style lang="scss">
.prism-editor__textarea {
  font-family: "JetBrains Mono", monospace;
  outline: none;
}
</style>
