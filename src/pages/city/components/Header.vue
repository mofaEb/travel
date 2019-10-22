<template>
  <div class="header">
    城市选择
    <router-link to="/" tag="span">
      <div class="iconfont header-back">&#xe66c;</div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header
    position: relative
    overflow: hidden
    height: $headerHeight
    line-height: $headerHeight
    text-align: center
    color: #ffffff
    background-color: $bgColor
    font-size: .32rem
    // margin: 0
    .header-back
      position: absolute
      width: .64rem
      text-align: center
      font-size: .4rem
      top: 0
      left: 0
</style>
