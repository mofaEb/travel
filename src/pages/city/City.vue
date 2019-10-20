<template>
  <div>
    <city-header></city-header>
    <city-search></city-search>
    <city-list :letter='letter' :cities="cities" :hotCities="hotCities"></city-list>
    <city-alphabet
      :cities="cities"
      @change="handleLetterChange"
    ></city-alphabet>
  </div>
</template>

<script>
import axios from 'axios'
import CityHeader from './components/Head'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'
export default {
  name: 'City',
  data () {
    return {
      hotCities: [],
      cities: {},
      letter: ''
    }
  },
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet
  },
  methods: {
    getCityInfo () {
      axios.get('/api/city.json')
        .then(this.handleGetCityInfoSucc)
    },
    handleGetCityInfoSucc (res) {
      const data = res.data.data
      this.hotCities = data.hotCities
      this.cities = data.cities
    },
    handleLetterChange (letter) {
      this.letter = letter
      // console.log(letter)
    }
  },
  mounted () {
    this.getCityInfo()
  }
}
</script>

<style lang="stylus" scoped>

</style>
