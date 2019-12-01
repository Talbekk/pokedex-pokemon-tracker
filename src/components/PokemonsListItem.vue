<template lang="html">
  <li v-on:click='handleClick'>{{upperCase(pokemon.name)}}</li>
</template>

<script>

import {eventBus} from "../main.js";

export default {
  name: 'pokemon',
  props: ["pokemon"],
  methods: {
    upperCase(name) {
      return name.charAt(0).toUpperCase() + name.slice(1);
    },
    handleClick(){
    const clickedPokemon = null;
    fetch(`${this.pokemon.url}`)
    .then(res => res.json())
    .then(data => eventBus.$emit("pokemon-clicked", data))
  }
  }
}
</script>

<style lang="css" scoped>
</style>
