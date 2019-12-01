<template lang="html">
  <div>
    <p>Pokemon:</p>
    <pokemons-list :pokemons='pokemons'></pokemons-list>
  </div>
</template>

<script>

import PokemonsList from "./components/PokemonsList.vue";

export default {
  name: "app",
  data() {
    return {
      pokemons: [],
      selectedPokemon: []
    }
  },
  components: {
    "pokemons-list": PokemonsList
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
  }
}
</script>

<style lang="css" scoped>
</style>
