<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area" v-show="show">
        <div class="title border-topbottom">当前城市</div>
        <div class="btn-list">
          <div class="btn-wrapper">
            <div class="btn">{{this.$store.state.city}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-show="show">
        <div class="title border-topbottom">热门城市</div>
        <div class="btn-list">
          <div class="btn-wrapper"
            v-for='hotCity in hotCities'
            :key='hotCity.id'
            @click="handleCityClick(hotCity.name)"
          >
            <div class="btn">{{ hotCity.name }}</div>
          </div>
        </div>
      </div>
      <div class="area"
        v-for="(list, alphabet) in cities"
        :key='alphabet'
        :ref="alphabet">
        <div class="title border-topbottom" v-show="show">{{ alphabet }}</div>
        <div class="item-list">
          <div class="item border-bottom"
            v-for="cityName in list"
            :key='cityName.id'
            @click="handleCityClick(cityName.name)"
          >
            {{ cityName | keyFilter(dbWord) }}
          </div>
        </div>
      </div>
      <div class="no-item border-bottom" v-show="noItemShow" ref="test">
        没有找到匹配数据
      </div>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import _ from 'Lodash'
export default {
  name: 'CityList',
  props: {
    hotCities: Array,
    cities: Object,
    letter: String,
    keyword: String
  },
  computed: {
    show () {
      if (this.dbWord) {
        return false
      } else {
        return true
      }
    },
    noItemShow () {
      if (this.cityNum === 0) {
        return true
      } else {
        return false
      }
    }
  },
  methods: {
    getKeyword () {
      this.dbWord = this.keyword
      this.cityNum = 0
      for (let i in this.cities) {
        this.cities[i].forEach((value) => {
          if (value.spell.indexOf(this.dbWord) > -1 || value.name.indexOf(this.dbWord) > -1) {
            this.cityNum++
          }
        })
      }
    },
    handleCityClick (city) {
      this.$store.commit('changeCity', city)
      this.$router.push('/')
    }
  },
  data () {
    return {
      cityNum: 0,
      dbWord: ''
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
    this.debouncedGetWord = _.debounce(this.getKeyword, 300)
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    },
    keyword (newWord) {
      this.debouncedGetWord()
    }
  },
  filters: {
    keyFilter (city, keyword, cityList) {
      // const keyword = this.keyword
      if (city.name.indexOf(keyword) >= 0 || city.spell.indexOf(keyword) >= 0) {
        return city.name
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .border-topbottom
    &:before
      border-color: #ccc
    &:after
      border-color: #ccc
  .border-bottom
    &:before
      border-color: #ccc
  .list
    overflow: hidden
    position: absolute
    top: 1.58rem
    bottom: 0
    left: 0
    right: 0
    .title
      line-height: .44rem
      background: #eee
      padding-left: .2rem
      color: #666
      font-size: .24rem
    .btn-list
      overflow: hidden
      padding: .1rem .6rem .1rem .1rem
      .btn-wrapper
        float: left
        width: 33.33%
        .btn
          margin: .1rem
          text-align: center
          border: .02rem solid #ccc
          border-radius: .06rem
          padding: .1rem 0
  .item-list
    .item
      line-height: .76rem
      padding-left: .2rem
  .no-item
    line-height: .76rem
    padding-left: .2rem
</style>
