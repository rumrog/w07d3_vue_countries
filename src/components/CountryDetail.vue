<template lang="html">
  <div v-if='country !== null'>
    <h3>{{ country.name }}</h3>
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.popukation}}</p>
  </div>
  
</template>

<script>
export default {
  name: 'country-detail',
  props: ['country']
}
</script>

<style lang='css' scoped>

</style>