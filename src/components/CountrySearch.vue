<template lang="html">
  <div class="">
    <label for="findCountry">Search for a country: </label>
    <input v-model="search" type="text" v-on:keyup="searchCountries">
  </div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name:'country-search',
  props:['countries'],
  data(){
    return{
      search:"",
      selectedCountry: null
    }
  },
  methods:{
    searchCountries: function(){
      eventBus.$emit('search-countries', this.search)
    }
  }

}
</script>

<style lang="css" scoped>
label, input{
  font-family: 'Mansalva', cursive;
  font-size: 2vw;
}
</style>
