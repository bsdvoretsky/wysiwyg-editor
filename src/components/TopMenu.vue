<script setup>
import IconBack from './icons/IconBack.vue'
import IconForward from './icons/IconForward.vue'
import IconTitle from './icons/IconTitle.vue'
import IconParagraph from './icons/IconParagraph.vue'
import IconImage from './icons/IconImage.vue'
import ButtonCopy from './buttons/ButtonCopy.vue'
import {ref} from 'vue';

const props = defineProps(['editor']);

const undo = () => {
    props.editor.chain().focus().undo().run();
}

const redo = () => {
    props.editor.chain().focus().redo().run();
}

const convertToTitle = () => {
    props.editor.chain().focus().setHeading({ level: 1 }).run()
}

const convertToParagraph = () => {
    props.editor.chain().focus().setParagraph().run()
}

const insertImage = () => {
    let url = prompt("URL")
    props.editor.chain().focus().setImage({ src: url }).run()
}

const copyHTML = () => {
    let html = document.getElementsByTagName('html')[0].innerHTML;
    navigator.clipboard.writeText(html);
}

const boxStyle = ref({
    display: 'flex',
    alignItems: 'center',
    marginTop: '77px',
    marginLeft: '107px',
});

const buttonStyle = ref({
    marginRight: '12px',
    cursor: 'pointer',
});
</script>

<template>
<div :style="boxStyle">
    <IconBack :style="buttonStyle" v-on:click="undo()"/>
    <IconForward :style="buttonStyle" v-on:click="redo()"/>
    <IconTitle :style="buttonStyle" v-on:click="convertToTitle()"/>
    <IconParagraph :style="buttonStyle" v-on:click="convertToParagraph()"/>
    <IconImage :style="buttonStyle" v-on:click="insertImage()"/>
    <ButtonCopy :style="{'margin-left': '7px', 'cursor': 'pointer'}" v-on:click="copyHTML()"/>
</div>
</template>