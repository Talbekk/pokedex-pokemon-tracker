<template lang="html">
  <li>
    <div>
    <img class="pokemon-icon" :src="pokemon.sprites.front_default"/>
    <button v-on:click="selectPokemon">View</button>
    <button v-on:click="removePokemon">Remove from team</button>
    </div>
  </li>
</template>

<script>

import { eventBus } from '../main.js';

export default {
  name: 'pokemon',
  props:['pokemon'],
  methods: {
    selectPokemon: function() {
      fetch(`${this.pokemon.url}`)
      .then(res => res.json())
      .then(data => eventBus.$emit("pokemon-selected", data));
    }
  }
}
</script>

<style lang="css" scoped>
</style>
