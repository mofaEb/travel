<template>
  <div class="search">
    <input class="search-input" v-model="keyword" placeholder="输入城市名或标签">
  </div>
</template>

<script>
export default {
  name: 'CitySearch',
  data () {
    return {
      keyword: ''
    }
  },
  // methods: {
  //   handleKeywordInput () {
  //     this.$emit("getKeyword", keyword)
  //   }
  // },
  watch: {
    keyword (keyword) {
      this.$emit('getKeyword', keyword)
      // console.log(keyword)
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .search
    // margin: 0
    padding: 0 .1rem
    height: .72rem
    background: $bgColor
    .search-input
      box-sizing: border-box
      width: 100%
      height: .62rem
      padding: 0 .1rem
      line-height: .62rem
      text-align: center
      border-radius: .06rem
      color: $txColor
</style>
