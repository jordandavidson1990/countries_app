<template lang="html">
  <div class="">

    <h1>🌍 Countries 🌎</h1>
    <div class="countries">
      <country-search :countries="countries"></country-search>
      <ul class="filteredList" v-if="filteredList !== []">
        <country-detail-filter  v-for="country in filteredList" :country="country"></country-detail-filter>
      </ul>
      <country-select :countries="countries"></country-select>
      <country-detail  v-if="selectedCountry" class="detail" :country="selectedCountry"></country-detail>
      <div class="full-list">
        <button v-if="!showAll" @click="clickList">Show Full List</button>
        <button v-if="showAll" @click="unclickList">Hide Full List</button>
        <countries-list v-if="showAll" :countries="countries"></countries-list>
      </div>
    </div>
  </div>
</template>

<script>
import { eventBus } from './main.js'
import CountryDetailFilter from './components/CountryDetailFilter';
import CountrySelect from './components/CountrySelect.vue';
import CountriesList from './components/CountriesList.vue'
import CountryDetail from './components/CountryDetail.vue'
import CountrySearch from './components/CountrySearch.vue'
export default {
  name: 'app',
  data(){
    return{
      countries: [],
      selectedCountry: null,
      showAll: false,
      search: ""
    }
  },
  mounted(){
    this.fetchCountries()

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country
    })

    eventBus.$on('search-countries', (search) => {
      this.search = search
    })
  },
  methods:{
    fetchCountries: function(){
      fetch('https://restcountries.eu/rest/v2/all')
      .then(res => res.json())
      .then(data => this.countries = data)
    },
    clickList: function(){
      this.showAll = true
    },
    unclickList: function(){
      this.showAll = false
    }
  },
  components:{
    "countries-list":CountriesList,
    "country-detail":CountryDetail,
    "country-select":CountrySelect,
    "country-search":CountrySearch,
    "country-detail-filter":CountryDetailFilter
  },
  computed: {
    filteredList() {
      return this.countries.filter(country => {
        return country.name.toLowerCase().includes(this.search.toLowerCase())
      })
    }
}
}

</script>

<style lang="css" scoped>
.filteredList{
  width: 25vw;
  max-height: 20vh;
  overflow-y: scroll;
  border: 1px solid black;
}
h1{
  text-align: center;
  font-family: 'Mansalva', cursive;
}
p, li{
  font-family: 'Mansalva', cursive;
}
country-select{
  margin-bottom: 10px;
}
.countries{
  display: flex;
  margin: auto;
  width: 50%;
  flex-wrap: wrap;
  justify-content: center;
  padding-top: 1vh;
}

.full-list{
  max-height: 25vh;
  overflow-y: scroll;
  width: auto;
  border: 2px black solid;
  background-color: grey;
  cursor: pointer;
  justify-content: center;
  display: flex;
  flex-wrap: wrap;
  padding-top: 1vw;
  margin: 1vh;
}
.detail{
  background-color: #f1f2f3;
  min-width: 38vw;
  text-align: center;
  border: 1px solid;
  margin-top: 1px;
}
body{
  background: beige;
}

</style>
