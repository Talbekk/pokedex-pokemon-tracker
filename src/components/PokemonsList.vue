<template lang="html">
<div id="pokemons-list" v-if='pokemons.length'>
  <pokemons-list-item v-for='(pokemon, index) in pokemons' :pokemon='pokemon' :key='index'></pokemons-list-item>

</div>
</template>

<script>
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
