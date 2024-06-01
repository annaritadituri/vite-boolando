<script>
    export default {
        name: 'Menu',
    }
</script>

<template>

    <button class="border-0"><i class="fas fa-user"></i></button>
    <button class="border-0"><i class="fas fa-heart"></i></button>
    <button class="border-0 pe-0"><i class="fas fa-cart-shopping"></i></button>
   
</template>

<style lang="scss">

@import '../assets/styles/main.scss';

button {
    color: $white;
    background-color: $bg_header;
}

</style>