<template lang="html">
<div id="pokemons-list" v-if='pokemons.length'>
  <ul>
  <pokemons-list-item v-for='(pokemon, index) in pokemons' :pokemon='pokemon' :key='index'></pokemons-list-item>
  </ul>
</div>
</template>

<script>
import PokemonsListItem from "./PokemonsListItem.vue"
export default {
  name: "pokemons-list",
  props: ["pokemons"],
  components: {
    "pokemons-list-item": PokemonsListItem
  }
}
</script>

<style lang="css" scoped>
</style>
