<template lang="html">
  <div>
    <p>Pokemon:</p>
    <pokemons-list :pokemons='pokemons'></pokemons-list>
    <pokemon-info :pokemon='this.selectedPokemon'></pokemon-info>
  </div>
</template>

<script>

import PokemonsList from "./components/PokemonsList.vue";
import PokemonInfo from "./components/PokemonInfo.vue"
import {eventBus} from "./main.js";

export default {
  name: "app",
  data() {
    return {
      pokemons: [],
      selectedPokemon: null
    }
  },
  components: {
    "pokemons-list": PokemonsList,
    "pokemon-info": PokemonInfo
  },
  methods: {

    getPokemons: function () {
      fetch('https://pokeapi.co/api/v2/pokemon/?limit=151')
      .then(res => res.json())
      .then(data => this.pokemons = data.results)
    }
  },
  mounted() {
    this.getPokemons();

    eventBus.$on("pokemon-clicked", pokemon => {
      this.selectedPokemon = pokemon;
  })
}
}
</script>

<style lang="css" scoped>
</style>
