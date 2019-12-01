<template lang="html">
<div>
<p>{{upperCase(pokemon.name)}}</p>
<p>Type: {{upperCase(pokemonTypes(pokemon.types))}}</p>
<p>Height: {{pokemon.height}}ft</p>
<p>Weight: {{pokemon.weight}}lbs</p>
<img :src="pokemon.sprites['front-default']"/>

</div>
</template>

<script>
export default {
  name: 'pokemon-info',
  props: ['pokemon'],
  methods: {
    upperCase(name) {
      return name.charAt(0).toUpperCase() + name.slice(1);
    },
    pokemonTypes(pokemonTypes) {
      if (pokemonTypes.length > 1) {
        return `${pokemonTypes[0]['type']['name']}/${pokemonTypes[1]['type']['name']}`;
      }
      else {
        return `${pokemonTypes[0]['type']['name']}`;
      }
    }
  }
}
</script>

<style lang="css" scoped>
</style>
