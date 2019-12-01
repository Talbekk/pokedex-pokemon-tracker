<template lang="html">
<div>
<p>{{upperCase(pokemon.name)}}</p>

</div>
</template>

<script>
export default {
  name: 'pokemon-info',
  props: ['pokemon'],
  methods: {
    upperCase(name) {
      return name.charAt(0).toUpperCase() + name.slice(1);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
