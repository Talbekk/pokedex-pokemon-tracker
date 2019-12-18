<template lang="html">
  <li v-if="this.caughtStatus || (!this.caughtStatus && !caughtFilter)">
  <div>
  <p>{{pokemon.id}}</p>
  <p>{{upperCase(pokemon.name)}}</p>
  <button v-on:click="handleClick">View</button>
  <div v-if='!caughtStatus'>
  <input type="checkbox" id="caught" v-model="caughtStatus">
  <label for="caught">Caught</label>
  </div>
  <button v-if="caughtStatus" v-on:click="addToTeam">Add to team</button>
  <img :src="pokemon.sprite">
  </div>
</li>
</template>

<script>

import {eventBus} from "../main.js";

export default {
  name: 'pokemon',
  props: ["pokemon", "caughtFilter"],
  data() {
    return {
      caughtStatus: false
    }
  },
  methods: {
    upperCase(name) {
      return name.charAt(0).toUpperCase() + name.slice(1);
    },
    // caughtPokemon() {
    //   this.caughtStatus =  true;
    //   eventBus.$emit("pokemon-caught", 1);
    // },
    handleClick(){
    fetch(`${this.pokemon.url}`)
    .then(res => res.json())
    .then(data => eventBus.$emit("pokemon-clicked", data))
  },
  addToTeam(){
  fetch(`${this.pokemon.url}`)
  .then(res => res.json())
  .then(data => eventBus.$emit("add-pokemon-to-team", data))

  }
}
}
</script>

<style lang="css" scoped>

li {
  display: flex;
  flex-direction: column;
  margin: 0.5em;
  padding: 1em;
  max-width: 20%;
  border: 2px solid #669999;
  border-radius: 30%;
  flex-grow: 1;
}

</style>
