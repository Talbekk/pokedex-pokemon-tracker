<template lang="html">
  <div id="team-list" v-if='pokemonTeam.length'>
  <p>Current Team:</p>
  <ol>
    <pokemon-team-member v-for='(pokemon, index) in pokemonTeam' :pokemon='pokemon' :key='index'></pokemon-team-member>
  </ol>
  </div>
</template>

<script>

import PokemonTeamMember from './PokemonTeamMember.vue';

export default {
  name: "pokemon-team",
  props:['pokemonTeam'],
  components: {
    "pokemon-team-member": PokemonTeamMember
  }
}
</script>

<style lang="css" scoped>
</style>
