<script setup>
const { cards } = defineProps(['cards']);
</script>
<template>
    <div class="card" v-for="{image, title, description} in cards">
        <div class="image">
            <div class="circle"></div>
            <img :src="image" :alt="title">
        </div>
        <div class="text">
            <h3>{{ title }}</h3>
            <p>{{ description }}</p>
        </div>
    </div>
</template>

<style scoped>
    div.cards div.card {
        width: 380px;
        height: 411px;
        border: 4px solid #D6C092;
        background: #FBF9F5 0% 0% no-repeat padding-box;
        box-shadow: 0px 6px 10px #CCC6B677;
        border-radius: 4px;
        opacity: 0.8;
        position: relative;
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
    }

    /* CSS dla kart */
    div.cards div.image {
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
    }
    div.card div.image {
        margin-top: 39px;
    }
    div.card div.circle {
        width: 135px;
        height: 135px;
        border-radius: 100%;
        background-color: #DDC1BC;
        position: absolute;
        z-index: -1;
        left: 67px;
        bottom: 4px;
    }
    div.cards div.text {
        padding: 30px 35px;
    }
    div.cards div.text h3 {
        color: #2D645A;
        font: normal normal bold 28px Poppins;
        margin-bottom: 10px;
    }
    div.cards div.text p {
        color: #000000;
        font: normal normal normal 16px Poppins;
    }
</style>