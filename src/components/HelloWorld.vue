<script lang="ts">
import { defineComponent } from 'vue';
import { Editor, rootCtx } from '@milkdown/core';
import { nord } from '@milkdown/theme-nord';
import { VueEditor, useEditor } from '@milkdown/vue';
import { commonmark } from '@milkdown/preset-commonmark';
export default defineComponent({
  components: {VueEditor},
  setup(){
    const editor = useEditor((root) =>
        Editor.make()
            .config((ctx) => {
              ctx.set(rootCtx, root);
            })
            .use(nord)
            .use(commonmark),
    );

    return{
      editor
    }
  }
})

</script>

<template>
  <VueEditor :editor="editor" />
</template>

<style scoped>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
