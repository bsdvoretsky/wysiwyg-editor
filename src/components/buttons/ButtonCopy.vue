<script setup>
import { ref } from 'vue';

const style = ref({
    color: '#639EFF',
    fontSize: '15px',
    fontStyle: 'normal',
    fontWeight: 400,
    lineHeight: '23px',
    userSelect: 'none',
})
</script>

<template>
    <span :style="style">Скопировать HTML</span>
</template>