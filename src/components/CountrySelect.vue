<template lang="html">
  <div class="select">
    <select v-model="selectedCountry" v-on:change="handleChange">
      <option disabled value="Select a country...">Select a country..</option>
      <option
      v-for="(country, index) in countries"
      :key="index"
      :value="country"
      >
      {{country.name}}</option>
    </select>
  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name:'countries-select',
  props:['countries'],
  data(){
    return{
      selectedCountry:null
    }
  },
  methods:{
    handleChange: function(){
      eventBus.$emit('country-selected', this.selectedCountry)
    }
  }
}
</script>

<style lang="css" scoped>
.select{
  margin-bottom: 10px;
}
select{
  font-size: 2vw;
}
</style>
