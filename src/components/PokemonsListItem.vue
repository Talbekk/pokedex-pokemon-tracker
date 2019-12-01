<template lang="html">
  <li>{{upperCase(pokemon.name)}}</li>
</template>

<script>
export default {
  name: 'pokemon',
  props: ["pokemon"],
  methods: {
    upperCase(name) {
      return name.charAt(0).toUpperCase() + name.slice(1);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
