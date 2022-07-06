<template>
    <PokeMon/>
</template>

<script>
    import PokeMon from '@/components/Pokemon.vue'

    export default {
        name: 'App',
        components: {
            PokeMon
        }
    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        color: #2c3e50;
        margin-top: 30px;
    }
    body {
        background-image: url(@/assets/pokemon-bg.jpeg);
        background-size: 100vw;
    }
</style>
