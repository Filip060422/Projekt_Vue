<script setup>
import HeaderComponent from './components/HeaderComponent.vue'
import ButtonComponent from './components/ButtonComponent.vue'
import CardComponent from './components/CardComponent.vue'
import BoxComponent from './components/BoxComponent.vue'
import FooterComponent from './components/FooterComponent.vue'
import QuestionModalComponent from './components/QuestionModalComponent.vue'

import { ref } from 'vue';

const isVisible = ref(true);

const toggleContainers = () => {
  isVisible.value = !isVisible.value;
};

</script>

<template>
    <div class="container " v-show="isVisible">
        <div class="first-page">
            <HeaderComponent />
            <div class="main-area">
                <section class="banner padding">
                    <div class="left">
                        <h2>Wiosna nadchodzi - zgarnij wiosenne gadżety od Mediaflex!</h2>
                        <div class="line"></div>
                        <p>Do wiosny jeden krok... weź udział w konkursie i wygraj gadżety, które z pewnością umilą coraz cieplejsze wiosenne popołudnia.</p>
                        <ButtonComponent :toggleContainers="toggleContainers"/>
                    </div>
                    <div class="right">
                        <img src="/icons/flowers.svg" alt="flowers">
                    </div>
                </section>
                <div class="mouse">
                    <img src="/icons/mouse-icon.svg" alt="mouse icon">
                </div>
            </div>
        </div>
        
        <div class="second-page padding">
            <h2 id="awards">Co możesz wygrać?</h2>
            <div class="cards">
                <CardComponent />
            </div>
            <ButtonComponent :toggleContainers="toggleContainers"/>
            <p><a href="#">Regulamin konkursu</a></p>
        </div>

        <div class="third-page padding">
            <h2 id="steps">Do Nagrody Dzielą Cię 3 Kroki!</h2>
            <div class="boxes">
                 <BoxComponent />
            </div>
            <ButtonComponent :toggleContainers="toggleContainers"/>
        </div>
        <FooterComponent />
    </div>
    <div class="container-modal padding " v-show="!isVisible">
        <div class="logo">
            <img src="/icons/logo.svg" alt="Logo">
        </div>
        <form action="" method="post" id="survey-form">
            <QuestionModalComponent />
        </form>
    </div>
</template>

<style scoped>
    @import url(./assets/main.css);

    div.first-page {
        max-width: 1920px;
        height: 1080px;
        background: #FBF9F5 0% 0% no-repeat padding-box;
    }
    section.banner {
    display: inline-flex;
    align-items: center;
    padding-top: 73px;
    }
    section div.left h2 {
        color: #2D645A;
        font-size: 42px;
        font-family: Abril Fatface;
        font-weight: 100;
    }
    section div.left div.line {
        width: 193px;
        border: 1px solid #EBBE45;
        margin: 30px 0;
    }
    section div.left p {
        font: normal normal normal 18px/32px Poppins;
        width: 586px;
        margin-bottom: 50px;
    }
    div.mouse {
        margin: auto;
        margin-top: 304px;
        width: 60px;
        height: 60px;
        background: #E1B9B5 0% 0% no-repeat padding-box;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 100%;  
    }

    div.second-page {
        margin-top: 100px;
        height: 918px;
    }
    div.second-page h2, div.third-page h2 {
        font-size: 48px;
        font-weight: bold;
        color: #543E3C;
        margin: 50px 0;
    }
    div.second-page div.cards {
        display: flex;
        justify-content: space-between;
    }
    div.second-page input, div.third-page input {
        margin: auto;
        margin-top: 50px;
        display: flex;
    }
    div.second-page p a{
        margin-top: 40px;
        display: flex;
        justify-content: center;
    }
    div.second-page a {
        color: #543E3C;
        display: flex;
        text-align: left;
        text-decoration: underline;
        font: normal normal 600 21px/117px Poppins;
        letter-spacing: 0.21px;
        color: #543E3C;
        justify-content: center;
        margin-top: 40px;
        margin-bottom: 100px;
    }

    div.third-page {
        background: #FBF9F5 0% 0% no-repeat padding-box;
        padding-top: 100px;
        padding-bottom: 100px;
    }
    div.third-page div.boxes {
        display: flex;
        justify-content: space-between;
    }

    /* Modal */
    div.container-modal {
        height: 100vh;
        width: 100%;
        padding-top: 40px;
        background-color: rgba(0,0,0,0.4);
        position: relative;
    }
</style>