<template lang="html">
  <div>
    <li @click="handleClick">🌎 {{country.name}}</li>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'list-item',
  props:['country'],
  methods:{
    handleClick: function(){
      eventBus.$emit('country-selected', this.country)
    }
  }
}
</script>

<style lang="css" scoped>
li{
  list-style: none;
  font-size: 2vw;
  color: beige;
}

</style>
