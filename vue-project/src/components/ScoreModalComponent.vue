<script setup>
import InputComponent from './InputComponent.vue'
import { ref, watchEffect } from 'vue'
const { score, NpsInvisible, toggleWindow } = defineProps(['score', 'NpsInvisible', 'toggleWindow']);

const checkedAll = ref(false);
const rules = ref(false);
const data = ref(false);
const dataTwo = ref(false);

const isChcecked = ref(false);
const isAlert = ref(false);

watchEffect(() => {
  if (checkedAll.value) {
    rules.value = true;
    data.value = true;
    dataTwo.value = true;
  }
  if(!checkedAll.value) {
    rules.value = false;
    data.value = false;
    dataTwo.value = false;
  }

});

watchEffect(() => {
    if (rules.value  && dataTwo.value) {
        isChcecked.value = !isChcecked.value;
    } else if (!checkedAll.value) {
        isChcecked.value = false;
    }
});
function handleClick(event) {
    if (isChcecked.value) {
        event.preventDefault();
        toggleWindow();
    }
};

const checkboxes = ref([
    {
         id: "all",
         v: checkedAll,
         required: false,
         label: 'Zaznacz wszystkie zgody'
    },
    {
         id: "rules",
         v: rules,
         required: true,
         label: '* Akceptuję <a href="#" style="color: #E1B9B5">regulamin konkursu</a>'
    },
    {
         id: 'data',
         v: data,
         required: false,
         label: 'Zgoda na przetwarzanie danych osobowych dla celów konkursu'
    },
    {
         id: 'dataTwo',
         v: dataTwo,
         required: true,
         label: '* Wyrażam zgodę na przetwarzanie podanych przeze mnie moich danych osobowych w zakresie imię, nazwisko, adres e-mail, numer PWZ, numer telefonu przez Administratora w celu organizacji i realizacji Konkursu.'
    }
]);
</script>
<template>
    <div class="modal-content modal-content-score">
                <div class="score">
                    <h2>Wiosna nadchodzi - konkurs Mediaflex</h2>
                    <h3>Dziękujemy za grę!</h3>
                    <h4>Twój wynik: <span class="final-result">{{ score }}/3</span></h4>
                    <h5>Aby grać o nagrody - zaakceptuj zgody i zapisz swój wynik.</h5>
                    <div class="images">
                        <div class="circle"></div>
                        <img src="/icons/prize-one.png" alt="">
                        <img src="/icons/prize-two.png" alt="">
                        <img src="/icons/prize-three.png" alt="">
                    </div>
                    <div class="checkbox">
                        <table>
                            <tr v-for="(checkbox, index) in checkboxes" :key="index">
                                <td><input type="checkbox" v-model="checkbox.v" :id="checkbox.id" class="check" :required="checkbox.required"></td>
                                <td><label :for="checkbox.id" v-html="checkbox.label"></label></td>
                            </tr>
                        </table>
                        <p>Klauzula informacyjna RODO <a href="#">czytaj więcej</a></p>
                        <p>* Pola obowiązkowe są oznaczone gwiazdką</p>
                        <div class="button">
                            <InputComponent class="end-button" @click="handleClick"/>
                        </div>
                    </div>
                </div>
            </div>
</template>

<style scoped>
div.modal-content.modal-content-score {
    height: 726px;
}
div.modal-content h2 {
    color: #2D645A;
    font-size: 42px;
    font-family: Abril Fatface;
    font-weight: 100;
    margin-bottom: 13px;
    color: #2D635A;
    font: normal normal normal 38px / 51px Abril Fatface;
}
div.modal-content div.score h3 {
    font: normal normal normal 28px/42px Poppins;
    color: #000000;
    margin-bottom: 19px;
}
div.modal-content div.score h4 {
    padding: 20px;
    font: normal normal 38px Poppins;
    border: 2px solid #E3E3E3;
    border-radius: 20px;
    width: 330px;
    margin-bottom: 48px
}
div.modal-content div.score h4 span {
    color: #E1B9B5;
    font-weight: bold;
}
div.modal-content div.score h5 {
    font: normal normal 20px/26px Poppins;
    margin-bottom: 21px;
}
div.modal-content div.score input {
    margin-right: 8px;
    width: 19px;
    height: 19px;
}
div.modal-content div.score label {
    font: normal normal 14px/21px Poppins;
}
div.modal-content div.score p {
    font: normal normal 14px/21px Poppins;
    margin-bottom: 23px;
}
div.modal-content div.score p a, div.modal-content div.score label a {
    font: normal normal 14px/21px Poppins;
    color: #E1B9B5;
}
div.modal-content div.score p a {
        margin-left: 10px;
}
div.modal-content div.score tr, td {
    display: flex;
    align-items: flex-start;
}
div.modal-content div.score tr {
    margin-bottom: 14px;
}
div.modal-content div.score div.submit p {
    margin-bottom: 0;
    font: normal normal 600 18px/27px Poppins;
    color: #543E3C;
}
div.modal-content div.score div.images img{
    position: absolute;
}
div.modal-content div.score div.images img:first-of-type {
    width: 77px;
    z-index: 2;
    right: 254px;
    top: 190px;
}
div.modal-content div.score div.images img:nth-of-type(2) {
    width: 124px;
    z-index: 3;
    right: 145px;
    top: 205px;
}
div.modal-content div.score div.images img:last-of-type {
    width: 206px;
    right: 50px;
    top: 262px;
    z-index: 4;
}
div.modal-content div.score div.images div.circle {
    width: 257px;
    height: 257px;
    position: absolute;
    z-index: 1;
    background: #DDC1BC 0% 0% no-repeat padding-box;
    border-radius: 100%;
    right: 78px;
    top: 120px;
}
</style>