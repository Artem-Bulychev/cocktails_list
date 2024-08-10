<script setup>
import { useRoute, useRouter } from 'vue-router';
import { Back } from '@element-plus/icons-vue';
import { computed } from 'vue';
import { ROUTER_PATHS } from '@/constants/router.js';

const props = defineProps({
    imgUrl: {
        type: String,
        required: true,

    }, 
    backFunc: {
        type: Function,
    }, 
    isBackButtonVisible: {
        type: Boolean,
        default: true,
    }
})

const route = useRoute();
const router = useRouter();

const routeName = computed(() => route.name);

function getForCoctailRandom() {
    router.push(ROUTER_PATHS.COCKTAIL_RANDOM);

    if (routeName.value === ROUTER_PATHS.COCKTAIL_RANDOM) {
        router.go();
    }
}

function goback() {
    props.backFunc ? props.backFunc() : router.go(-1);
}
</script>

<template>
<div class="root">
    <div :style="`background-image: url(${imgUrl})`"class="img"></div>
    <div class="main">
        <div class="btns">
            <el-button v-if="isBackButtonVisible" type="primary" :icon="Back" circle class="back" @click="goback"/>
            <el-button class="btn">Get random cocktail</el-button>
        </div>
        <el-button class="btn" @click="getForCoctailRandom">Get random cocktail</el-button>
        <slot></slot>
    </div>
</div>
</template>

<style lang="sass" scoped>
@import '../assets/styles/main'

.root 
    display: flex
    background-color: $background
    min-height: 100vh

.img 
    width: 50%
    background-repeat: no-repeat
    background-position: 50% 50%
    background-size: cover

.main
    width: 50%
    padding: 32px 40px 
    position: relative

.btn
    position: absolute
    top: 32px 
    right: 40px
    background-color: $accent
    border-color: $accent
    color: $text
    font-size: 16px
    font-family: 'Raleway', 'Arial', sans-serif

    &:hover,
    &:active
        background-color: darken($accent, 10)
        border-color: darken($accent,10)

.btns
    display: flex
    justify-content: space-between
    align-items: center

.back 
    background-color: transparent
    border-color: #fff

    &:hover
        border-color: $accent
</style>
