<script>
    import Header from './components/HeaderComponent.vue'
    import ProductsList from './components/ProductsList.vue'
    import Footer from './components/FooterComponent.vue'
    export default {
        name: 'MyApp',
        components: {
            Header,
            ProductsList,
            Footer,
        },
    }
</script>

<template>

    <Header />
    <ProductsList />
    <Footer />
        
   
</template>

<style lang="scss">
@import './assets/styles/main.scss';

</style>
