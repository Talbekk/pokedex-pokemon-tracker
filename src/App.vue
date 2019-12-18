<template lang="html">
  <div>
    <p>Pokedex:</p>
    <p>Total Pokemon: {{pokemonCount}}</p>
    <pokemon-team :pokemonTeam='pokemonTeam'></pokemon-team>
    <!-- <p>Total Caught: {{pokemonCaught}}</p> -->
    <button type="button" v-on:click="caughtFilter = !caughtFilter">{{ caughtFilter ? "Show All" : "Show Caught" }}</button>
    <div id="main-container">
    <pokemons-list :pokemons='pokemons' :caughtFilter="caughtFilter"></pokemons-list>
    <div v-if='selectedPokemon'>
    <pokemon-info :pokemon='selectedPokemon'></pokemon-info>
    </div>
  </div>
  </div>
</template>

<script>

import PokemonsList from "./components/PokemonsList.vue";
import PokemonTeam from "./components/PokemonTeam.vue";
import PokemonInfo from "./components/PokemonInfo.vue";
import {eventBus} from "./main.js";

export default {
  name: "app",
  data() {
    return {
      pokemons: [],
      selectedPokemon: null,
      caughtFilter: false,
      pokemonTeam: []
    }
  },
  components: {
    "pokemons-list": PokemonsList,
    "pokemon-info": PokemonInfo,
    "pokemon-team": PokemonTeam
  },
  methods: {

    getPokemons: function () {
      fetch('https://pokeapi.co/api/v2/pokemon/?limit=151')
      .then(res => res.json())
      .then(pokemonData => this.pokemons = pokemonData.results)
  }
  },
  mounted() {
    this.getPokemons();

    eventBus.$on("pokemon-clicked", pokemon => {
      this.selectedPokemon = pokemon;
  }),
    eventBus.$on("add-pokemon-to-team", pokemon => {
      this.pokemonTeam.push(pokemon);
})

},
computed: {
  pokemonCount: function(){
    return this.pokemons.length;
  }
    // pokemonTeam: function(){
    // return this.pokemons.filter(pokemon => pokemon.isChosen);

  }
}


    //     { pokemonData.forEach(pokemon => (pokemon.isChosen = false));
    //     this.pokemons = pokemonData;
    // })
</script>

<style lang="css" scoped>
#main-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
</style>
