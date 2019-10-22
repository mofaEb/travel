<template>
  <div>
    <home-header></home-header>
    <home-swiper :swiperList="swiperList"></home-swiper>
    <home-icons :imgList="imgList"></home-icons>
    <home-recommend :recommendList="recommendList"></home-recommend>
    <home-research :itemList="itemList"></home-research>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeResearch from './components/Research'
import axios from 'axios'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeResearch
  },
  data () {
    return {
      recommendList: [],
      swiperList: [],
      imgList: [],
      itemList: []
    }
  },
  methods: {
    getHomeInfo () {
      axios.get('api/index.json')
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      if (res.data) {
        const data = res.data.data
        this.recommendList = data.recommendList
        this.swiperList = data.swiperList
        this.imgList = data.iconList
        this.itemList = data.weekendList
        // console.log(data)
      }
    }
  },
  mounted () {
    this.getHomeInfo()
  }
}
</script>

<style>

</style>
