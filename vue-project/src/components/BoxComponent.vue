<script setup>
const { boxes } = defineProps(['boxes']);
</script>
<template>
    <div class="box" v-for="(box, index) in boxes" :key="index">
        <div class="image">
            <div class="circle"></div>
                <img :src="box.image" :alt="'Ikona ' + (index + 1)">
                <h3>Krok {{ index + 1 }}</h3>
            </div>
            <div class="text">
                <h3>{{ box.title }}</h3>
            </div>
        </div>
</template>

<style scoped>
    div.boxes div.box {
        width: 400px;
        height: 285px;
        background: #FBF9F5 0% 0% no-repeat padding-box;
        box-shadow: 0px 6px 10px #CCC6B677;
        border-top: 4px solid #D6C092;
        border-bottom: 4px solid #D6C092;
        border-left: 4px solid #D6C092;
        opacity: 0.8;
        position: relative;
        z-index: 3;
    }
    div.boxes div.box::before {
        content: '';
        position: absolute;
        top: -4px;
        right: -36px;
        width: 0;
        height: 0;
        background: #FBF9F5 0% 0% no-repeat padding-box;
        border-top: 142px solid transparent;
        border-left: 40px solid #FBF9F5;
        border-bottom: 143px solid transparent;
        z-index: 2;
    }
    div.boxes div.box::after {
        z-index: -1;
        content: '';
        position: absolute;
        top: -4px;
        right: -40px;
        width: 0;
        height: 0;
        background: #FBF9F5 0% 0% no-repeat padding-box;
        border-top: 142px solid transparent;
        border-left: 40px solid #D6C092;
        border-bottom: 143px solid transparent;
        z-index: 1;
    }

    /* div.boxes div.box:first-of-type, div.boxes div.box:nth-of-type(2) {
        margin-right: 50px;
    } */
    div.box div.image {
        display: flex;
        align-items: center;
        margin-left: 50px;
        margin-top: 44px;
    }
    div.box div.image h3 {
        color: #543E3C;
        font: normal normal  35px Poppins;
        margin-left: 44px;
    }
    div.box:last-of-type div.image h3 {
        margin-left: 58px;
    }
    div.box div.circle {
        width: 96px;
        height: 96px;
        border-radius: 100%;
        background-color: #DDC1BC;
        position: absolute;
        z-index: -1;
        left: 35px;
        top: 30px;
    }
    div.box div.text {
        margin: 50px 0 30px 35px;
    }
    div.box div.text h3 {
        color: #2D645A;
        font: normal normal bold 28px Poppins;
    }
    div.box:nth-of-type(2) div.text h3 {
        max-width: 309px;
    }
</style>