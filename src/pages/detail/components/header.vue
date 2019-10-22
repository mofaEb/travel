<template>
  <div>
    <router-link
      tag="div"
      to='/'
      class="header-abs"
      v-show="showAbs">
      <div class="iconfont .header-abs-back">&#xe66c;</div>
    </router-link>
    <div
      class="header-fixed"
      v-show="!showAbs"
      :style="opacityStyle">
      景点详情
      <router-link to="/" tag="span">
        <div class="iconfont header-fixed-back">&#xe66c;</div>
      </router-link>
    </div>
  </div>

</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = { opacity }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header-abs
    position: absolute
    left: .2rem
    top: .2rem
    width: .8rem
    height: .8rem
    border-radius: .4rem
    line-height: .8rem
    text-align: center
    background: rgba(0, 0, 0, .6)
    color: white
    .header-abs-back
      font-size: .2rem
   .header-fixed
    position: fixed
    top: 0
    left: 0
    right: 0
    overflow: hidden
    height: $headerHeight
    line-height: $headerHeight
    text-align: center
    color: #ffffff
    background-color: $bgColor
    font-size: .32rem
    // margin: 0
    .header-fixed-back
      position: absolute
      width: .64rem
      text-align: center
      font-size: .4rem
      top: 0
      left: 0
</style>
