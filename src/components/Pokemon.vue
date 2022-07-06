<template>
    <div class="ppal text-center">
        <img alt="Vue logo" src="@/assets/logo.png"  width="500">
        <h1 class="">Poke <span>DEX</span></h1>
        <form class="d-flex justify-content-center mt-4">
            <label class="my-0 align-self-center">Nombre:</label>
            <input class="mx-3" type="text" v-model="pokemon.name">
            <button class="btn-primary btn-sm" @click.prevent="fetchPokemon">Buscar</button>
        </form>
        <img :src="image"  alt="pokemon_image" width="150">
        <img :src="image2" alt="pokemon_image" width="150">

        <div class="container">
            <div class="row justify-content-center">
                <div class="col-3 text-start">
                    <h5 class="fw-bold">Habilidades:</h5>
                    <ul class=" my-0" v-for="(habilidad, index) in habilidades" :key="index">
                        <li>{{habilidad.ability.name}}</li>
                    </ul>
                </div>
                <div class="col-2 text-start">
                    <h5 class="fw-bold">Movimientos:</h5>
                    <ul class=" my-0" v-for="(movi, index) in movimientos" :key="index">
                        <li>{{movi.move.name}}</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'PokeMon',
        // props: { },
        data: function() {
            return {
                pokemon: {
                    name: "pikachu",
                    sprites: {},
                    abilities: [],
                    moves: [],
                }
            }
        },
        computed: {
            image(){
                return this.pokemon.sprites.front_default
            },
            image2(){
                return this.pokemon.sprites.back_default
            },
            habilidades(){
                return this.pokemon.abilities
            },
            movimientos(){
                return this.pokemon.moves
            },
        },

        methods: {
            async fetchPokemon(){
                try{
                    let response = await fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemon.name}`)
                    if(!response.ok) throw ("Error en petición")

                    let json = await response.json()
                    console.log(json)
                    this.pokemon = json
                }

                catch(error){
                    console.log(error)
                }
            }
        },

        // watch: {},
        // components: {},
        // mixins: [],
        // filters: {},
        // -- Lifecycle Methods
        created(){
            this.fetchPokemon()
        }
        // -- End Lifecycle Methods

    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h1 {
        color: red;
        font-weight: 900;
        font-size: 42px;
    }
    span {
        color: blue;
    }
    label {
        color: black;
        font-weight: 800;
    }
    .row {
        color: black;
    }
</style>