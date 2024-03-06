<script setup>
import { ref } from 'vue';
// import { modals } from './modals.js';
const modals = ref([
    {
        question: 'W którym roku powstał Mediaflex?',
        answerA: '2007',
        answerB: '2008',
        answerC: '2009',
        status: 'one'
    },
    {
        question: 'Firmową wartością nie jest:',
        answerA: 'Jakość',
        answerB: 'Rozsądek',
        answerC: 'Komunikacja',
        status: 'two'
    },
    {
        question: 'Biuro Mediaflex znajduje się w:',
        answerA: 'Krakowie',
        answerB: 'Szczecinie',
        answerC: 'Rzeszowie',
        status: 'three'
    }
]);

// const modalsData = ref(modals);
</script>
<template>
    <div class="test" v-for="modal in modals">
    <div class="answer"  v-for="answer in modal">
        <img src="/icons/flower-icon.svg" alt="Ikona kwiatka" class="image-answer">
        <p>A</p>
        <input type="button" :value="answer.answerA" class="basic-border inputs-color">
    </div>
</div>
    <!-- <div class="answer"  >
        <img src="/icons/flower-icon.svg" alt="Ikona kwiatka" class="image-answer">
        <p>A</p>
        <input type="button" :value="modals.answerA" class="basic-border inputs-color">
        
    </div>
    <div class="answer"  >
        <img src="/icons/flower-icon.svg" alt="Ikona kwiatka" class="image-answer">
        <p>A</p>
        <input type="button" :value="modals.answerA" class="basic-border inputs-color">
        
    </div> -->
</template>

<style scoped>
    div.answer {
        position: relative;
        margin-bottom: 20px;
        display: flex;
        height: 75px;
        align-items: center;
    }
    div.answer img {
        position: absolute;
        z-index: -1;
        left: 0;
        top: 0;
    }
    div.answer p {
        color: #FFFFFF;
        font: normal normal bold 24px/26px Roboto;
        margin: 0 56px 0 26px;
    }
    div.answer input {
        width: 909px;
        height: 60px;
        background-color: #FFFFFF;
        border-radius: 10px;
        padding: 10px 25px;
        text-align: left;
        font: 18px Poppins;
        cursor: pointer;
    }
</style>