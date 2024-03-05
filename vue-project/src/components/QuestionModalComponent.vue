<script setup>
import ModalAnswerComponent from './ModalAnswerComponent.vue'
import { ref } from 'vue';
import { modals } from './modals.js';

const modalsData = ref(modals);



</script>
<template>
    <div class="modal-content " v-for="(modal, index) in modalsData" :key="index">
        <div class="first-question">
            <h2>Wiosna nadchodzi - konkurs Mediaflex</h2>
            <h3>Pytanie {{ index + 1 }}/3</h3>
            <h4>{{ modal.question }}</h4>    
                <div class="answers">
                    <ModalAnswerComponent />
                </div>
                <div class="bottom">
                    <button type="button" class="last-question" :class="{'hidden': modal.status == 'one'}"><img src="/icons/back-icon.svg" alt=""> <p>POPRZEDNIE PYTANIE</p></button>
                    <p class="alert alert-one hidden">Prosimy o zaznaczenie odpowiedzi!</p>
                    <div class="button">
                        <button type="submit" v-if="modal.status == 'three'">ZAKOŃCZ QUIZ</button>
                        <button type="button" v-else class="submit submit-one"><p>NASTĘPNE PYTANIE</p> <img src="/icons/next-icon.svg" alt=""></button>
                    </div>
                </div>
            </div>
        </div>
</template>

<style scoped>
    div.button button.none {
        display: none;
    }
    div.modal-content {
        width: 1088px;
        height: 600px;
        background-color: #FFFFFF;
        border-radius: 20px;
        z-index: 1;
        position: absolute;
        top: 180px;
        left: 416px;
        padding: 40px 40px 40px 35px;
    }
    div.modal-content h2 {
        color: #2D635A;
        font: normal normal normal 38px/51px Abril Fatface;
        margin-bottom: 13px;
    }
    div.modal-content h3 {
        color: #E1B9B5;
        font: normal normal 600 21px/28px Poppins;
        margin-bottom: 19px;
    }
    div.modal-content h4 {
        font: normal normal 20px/26px Poppins;
        margin-bottom: 48px;
    }
    div.answers div.answer {
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

    div.button button {
        padding: 18px 32px;
        display: flex;
        align-items: center;
        background-color: #E1B9B5;
        box-shadow: 0px 3px 6px #00000029;
        border-radius: 40px;
        border: none;
        cursor: pointer;
        font: normal normal 600 18px/27px Poppins;
        color: #543E3C;
    }
    div.button button img {
        margin-left: 18px;
    }
    div.button div.end-button {
        display: flex;
        justify-content: flex-end;
    }
    div.modal-content div.submit p {
        font: normal normal 600 18px/27px Poppins;
        color: #543E3C;
    }
    div.modal-content div.submit img {
        margin-left: 18px;
    }
    button.last-question {
        display: flex;
        align-items: center;
        cursor: pointer;
    }
    button.last-question p {
        margin-left: 18px;
        color: #E1B9B5;
        font: normal normal 16px Roboto;
    }
    button.last-question img {
        height: 13px;
    }
    div.button p.alert, div.bottom p.alert {
        color: red;
    }
    div.first-question div.bottom {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>