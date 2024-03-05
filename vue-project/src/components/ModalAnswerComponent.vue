<script setup>
import { ref } from 'vue';
import { modals } from './modals.js';

const modalsData = ref(modals);

</script>
<template>
    <div class="answer"  v-for="(modal, index) in modalsData" :key="index">
        <img src="/icons/flower-icon.svg" alt="Ikona kwiatka" class="image-answer">
        <p>A</p>
        <input type="button" :value="modal.answerA" class="basic-border inputs-color">
    </div>
</template>