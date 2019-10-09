<template lang="html">
  <div>
    <img :src="country.flag" alt="">
    <h3>{{country.name}}</h3>
    <p> 🏙 Capital - {{country.capital}}</p>
    <p>🕴 Population - {{country.population}}</p>
  </div>
</template>

<script>
export default {
  name: 'country-detail',
  props:['country']
}
</script>

<style lang="css" scoped>
h3, p{
  font-family: 'Mansalva', cursive;
}
img{
  max-width: 10vw;
}
</style>
