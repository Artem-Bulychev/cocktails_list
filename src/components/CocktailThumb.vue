<script setup>
const props = defineProps({
  cocktail: {
    type: Object,
    required: true,
  },  
});
</script>

<template>
<div class="root">
    <RouterLink :to="`/cocktails/${cocktail.idDrink}`">
    <div :style="`background-image: url(${cocktail.strDrinkThumb})`" class="pic"></div>
    </RouterLink>
    <RouterLink :to="`/cocktails/${cocktail.idDrink}`">
    <div class="name">{{ cocktail.strDrink }}</div>
    </RouterLink>
</div>
</template>

<style lang="sass" scoped>
@import '../assets/styles/main'

.root
    width: calc( (100% - 76px) / 3)
    margin-right: 38px
    margin-bottom: 20px

    &:nth-child(3n + 3)
        margin-right: 0px

.pic
    width: 120px
    height: 120px
    background-repeat: no-repeat
    background-position: 50% 50%
    background-size: 100%
    margin: 0 auto

.name
    width: 100%
    white-space: nowrap
    overflow: hidden
    text-overflow: ellipsis
    padding-top: 15px
    letter-spacing: 0.1em

</style>