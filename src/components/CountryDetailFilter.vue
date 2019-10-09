<template lang="html">
  <li @click="handleClick">🌍 {{country.name}}</li>
</div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name:'country-detail-filter',
  props:['country'],
  methods:{
    handleClick: function(){
      console.log('click');
      eventBus.$emit('country-selected', this.country)
    }
  }
}
</script>

<style lang="css" scoped>
li{
  font-family: 'Mansalva', cursive;
  cursor: pointer;
  list-style: none;
}


</style>
