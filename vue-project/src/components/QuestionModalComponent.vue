<script setup>
import { ref } from 'vue'
import ScoreModalComponent from './ScoreModalComponent.vue'
import InputComponent from './InputComponent.vue'
import NpsSurveyComponent from './NpsSurveyComponent.vue'
const { modals, checkboxes } = defineProps(['modals', 'checkboxes']);

const score = ref(0);

    const selectAnswer = (answer, modal) => {
        modal.selectedAnswer = answer;
    };

    const goToNextQuestion = (modalIndex) => {
    const modal = modals[modalIndex];
    if (modal.selectedAnswer) {
        if (modalIndex < modals.length - 1) {
            modal.status = 'answered';
            modals[modalIndex + 1].status = 'active';
        }
    } else {
        modal.showAlert = true;
    }
};
    const goToPreviousQuestion = (modalIndex) => {
        if (modalIndex > 0) {
            modals[modalIndex].status = 'answered';
            modals[modalIndex - 1].status = 'active';
            modals[modalIndex -1].showAlert = false;
        }
    };

    const isVisible = ref(false);
    const goToNextModal = (modalIndex) => {
        
        if (modals[modalIndex].selectedAnswer) {
            if(modalIndex === 2) {
                modals[modalIndex].status = 'answered';
                isVisible.value = !isVisible.value
                modals.forEach(modal => {
                    if (modal.selectedAnswer === modal.correctAnswer) {
                        score.value++;
                    }
                });
            }
        } else {
            modals[modalIndex].showAlert = true;
        }
    }

</script>
<template>
    <div class="modal-content " v-for="(modal, index) in modals" :key="index" v-show="modal.status === 'active'">
        <div class="first-question">
            <h2>Wiosna nadchodzi - konkurs Mediaflex</h2>
            <h3>Pytanie {{ index + 1 }}/3</h3>
            <h4>{{ modal.question }}</h4>    
                <div class="answers">
                    <div class="answer" v-for="(answer, answerIndex) in ['A', 'B', 'C']" :key="answerIndex">
                     <img class="image_answer"  :src="modal.selectedAnswer === answer ? '/icons/flower-icon-color.svg' : '/icons/flower-icon.svg'" alt="Flower Icon" >
                     <p>{{ answer }}</p>
                     <input class="border-two input-color basic-border" type="button" :value="modal['answer' + answer]" :class="{ 'active-border': modal.selectedAnswer === answer }" @click="selectAnswer(answer, modal)">
                 </div>
                
            </div>
                </div>
                <div class="bottom">
                    <button type="button" class="last-question" @click="goToPreviousQuestion(index)" :class="{'hidden': index == 0}"><img src="/icons/back-icon.svg" alt=""> <p>POPRZEDNIE PYTANIE</p></button>
                    <p class="alert" v-show="modal.showAlert">Prosimy zaznaczyć odpowiedź</p>
                    <div class="button">
                        <InputComponent  @click="goToNextModal(index)" v-if="index == 2"/>
                        <button type="button" @click="goToNextQuestion(index)" v-else class="submit submit-one"><p>NASTĘPNE PYTANIE</p> <img src="/icons/next-icon.svg" alt=""></button>
                    </div>
                </div>
        </div>
        <ScoreModalComponent v-show="isVisible" :score="score"/>
        <!-- <NpsSurveyComponent /> -->
</template>

<style scoped>
    div.button button.none {
        display: none;
    }
    div.bottom {
        display: flex;
        justify-content: space-between;
        align-items: center;
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
        display: block;
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

    .basic-border {
    border: 2px solid #EAEAEA;
}
.active-border {
    border: 3px solid #E1B9B5;
}
.hidden {
    visibility: hidden;
}
.border-answer-color {
    color: #543E3C;
}
</style>