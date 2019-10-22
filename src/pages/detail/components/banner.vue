<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" :src="bannerImg" />
      <div class="banner-info">
        <div class="banner-title">{{ sightName }}</div>
        <div class="banner-num">
          <span class="iconfont banner-icon">&#xe6df;</span>
          {{ gallaryImgs.length }}
          </div>
      </div>
    </div>
    <common-gallary
      :imgs="gallaryImgs"
      v-show="showGallary"
      @close="handleBannerClick"
    ></common-gallary>
  </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
export default {
  name: 'DetailBanner',
  props: {
    bannerImg: String,
    sightName: String,
    gallaryImgs: Array
  },
  data () {
    return {
      showGallary: false,
      imgs: ['https://imgs.qunarzz.com/sight/p0/1506/f6/f6b727f036fe5d6d.water.jpg_r_800x800_94ccd288.jpg', 'https://imgs.qunarzz.com/sight/p0/1905/20/2049ae4ed7942d6fa3.img.jpg_r_800x800_d08761b4.jpg']
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallary = !this.showGallary
    }
  },
  components: {
    CommonGallary
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position: relative
    overflow: hidden
    height: 0
    padding-bottom: 55%
    .banner-img
      width: 100%
    .banner-info
      display: flex
      position: absolute
      left: 0
      right: 0
      bottom: 0
      line-height: .6rem
      color: #fff
      background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8))
      .banner-title
        flex: 1
        font-size: .32rem
        padding: 0 .2rem
      .banner-num
        height: .32rem
        margin-top: .14rem
        padding: 0 .4rem
        line-height: .32rem
        border-radius: .2rem
        background: rgba(0, 0, 0, .8)
        font-size: .24rem
        .banner-icon
          font-size: .24rem
</style>
