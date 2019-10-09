<template lang="html">
  <div class="">
    <list-item v-for="(country, index) in countries" :country="country" :key="index"></list-item>
  </div>
</template>

<script>
import ListItem from './ListItem.vue'
import CountrySearch from './CountrySearch'
export default {
  name:'countries-list',
  props:['countries'],
  components:{
    "list-item":ListItem,
    "country-search":CountrySearch
  }
}
</script>

<style lang="css" scoped>

</style>
