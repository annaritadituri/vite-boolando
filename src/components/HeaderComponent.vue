<script>
    import Logo from '../components/LogoComponent.vue'
    import Section from '../components/SectionComponent.vue'
    import Menu from '../components/MenuComponent.vue'
    export default {
        name: 'Header',
        components: {
            Logo,
            Section,
            Menu,
        }
    }
</script>

<template>

    <header>

        <div class="container">

            <div class="row align-items-center text-center py-3">

                <div class="col-3 left text-start ps-0">
                    <Section />
                </div>
                <div class="col-6 center">
                    <Logo />
                </div>
                <div class="col-3 right text-end pe-0">
                    <Menu />
                </div>

            </div>

        </div>

    </header>
   
</template>

<style scoped lang="scss">

@import '../assets/styles/main.scss';

header {
    background-color: $bg_header;
    color: $white;
}

</style>
