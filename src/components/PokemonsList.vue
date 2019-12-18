<template lang="html">
<div id="pokemons-list" v-if='pokemons.length'>
  <ol>
  <pokemons-list-item v-for='(pokemon, index) in pokemons' :pokemon='pokemon' :caughtFilter="caughtFilter" :key='index'></pokemons-list-item>
</ol>
</div>
</template>

<script>
import PokemonsListItem from "./PokemonsListItem.vue"
export default {
  name: "pokemons-list",
  props: ["pokemons", "caughtFilter"],
  components: {
    "pokemons-list-item": PokemonsListItem
  }
}
</script>

<style lang="css" scoped>

ol {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
</style>
