<template>
  <div id="app">
    <h1>Countries</h1>
    <countries-list :countries='countries'></countries-list>
    <country-detail :country='selectedCountry'></country-detail>
  </div>
</template>

<script>
import CountryDetail from './components/CountryDetail.vue'
import CountriesList from './components/CountriesList.vue'
import ListComponent from './components/ListComponent.vue'
import {eventBus} from './main.js'

export default {
  name: 'App',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country) => {
      console.log(country.name);
      
      this.selectedCountry = country
    })
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

li {
  list-style-type: none;
}
</style>
