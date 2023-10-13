<script setup>
import TopMenu from './components/TopMenu.vue'
import StarterKit from '@tiptap/starter-kit'
import Image from '@tiptap/extension-image'
import { useEditor, EditorContent } from '@tiptap/vue-3'
import { ref } from 'vue';

const styleEditor = ref({
  color: '#EAEAEA',
  fontFamily: 'Roboto',
  fontSize: '15px',
  fontStyle: 'normal',
  fontWeight: '400',
  lineHeight: '23px',
  marginLeft: '107px',
  marginTop: '31px',
  width: '651px',
  height: '100%',
  border: 'none',
});

const editor = useEditor({
  content: '<h1>Смотрите какие обезьянки</h1>',
  extensions: [StarterKit, Image],
});
</script>

<template>
<main>
  <TopMenu :editor="editor"/>
  <editor-content :editor="editor" :style="styleEditor"/>
</main>
</template>

<style scoped>
main {
  width: 960px;
  background-color: #1E1E1E;
}
</style>
