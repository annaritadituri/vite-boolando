<script>
    import Header from './components/HeaderComponent.vue'
    import ProductsList from './components/ProductsList.vue'
    export default {
        name: 'MyApp',
        components: {
            Header,
            ProductsList,
        },
    }
</script>

<template>

    <Header />
    <ProductsList />
        
   
</template>

<style lang="scss">
@import './assets/styles/main.scss';

</style>
