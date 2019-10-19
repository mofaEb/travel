<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <!-- slides -->
      <swiper-slide v-for="(page, index) in pages" :key="index">
        <div class="icon" v-for="item of page" :key="item.id">
          <div class="icon-img" >
            <img class='icon-img-content' :src="item.url">
          </div>
          <p class="icon-desc">{{ item.title }}</p>
        </div>
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  data () {
    return {
      swiperOption: {
        pagination: {}
      },
      imgList: [
        {
          id: '01',
          url: '//s.qunarzz.com/homenode/images/touchheader/hotel.png',
          title: '酒店'
        }, {
          id: '02',
          url: '//s.qunarzz.com/homenode/images/touchheader/flight.png',
          title: '机票'
        }, {
          id: '03',
          url: '//s.qunarzz.com/homenode/images/touchheader/package.png',
          title: '度假'
        }, {
          id: '04',
          url: '//s.qunarzz.com/homenode/images/touchheader/train.png',
          title: '火车票'
        }, {
          id: '05',
          url: '//s.qunarzz.com/homenode/images/touchheader/innBnb.png',
          title: '民宿客栈'
        }, {
          id: '06',
          url: '//s.qunarzz.com/homenode/images/touchheader/bargainflight.png',
          title: '低价机票'
        }, {
          id: '07',
          url: '//s.qunarzz.com/homenode/images/touchheader/group.png',
          title: '特惠酒店'
        }, {
          id: '08',
          url: '//s.qunarzz.com/homenode/images/touchheader/haiwai.png',
          title: '海外酒店'
        }, {
          id: '09',
          url: '//s.qunarzz.com/homenode/images/touchheader/bus.png',
          title: '汽车票船票'
        }, {
          id: '10',
          url: '//s.qunarzz.com/homenode/images/touchheader/tuan.png',
          title: '旅行团购'
        }, {
          id: '11',
          url: '//s.qunarzz.com/homenode/images/touchheader/freeTravel.png',
          title: '自由行'
        }, {
          id: '12',
          url: '//s.qunarzz.com/homenode/images/touchheader/car.png',
          title: '专车自驾'
        }, {
          id: '13',
          url: '//s.qunarzz.com/homenode/images/touchheader/jr.png',
          title: '金融理财'
        }, {
          id: '14',
          url: '//s.qunarzz.com/homenode/images/touchheader/card.png',
          title: '保险车险'
        }, {
          id: '15',
          url: '//s.qunarzz.com/homenode/images/touchheader/oversea.png',
          title: '换外币'
        }, {
          id: '16',
          url: '//s.qunarzz.com/homenode/images/touchheader/youlun.png',
          title: '邮轮'
        }
      ]
    }
  },
  computed: {
    pages () {
      const pages = []
      this.imgList.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  @import '~styles/mixins.styl'
  .icons >>> .swiper-container
    height: 0
    padding-bottom: 50%
  .icons
    margin-top: .1rem
    .icon
      position: relative
      overflow: hidden
      float: left
      height: 0
      width: 25%
      padding-bottom: 25%
      .icon-img
        position: absolute
        top: 0
        left: 0
        right: 0
        bottom: .44rem
        box-sizing: border-box
        padding: .1rem
        .icon-img-content
          display: block
          height: 100%
          margin: 0 auto
      .icon-desc
        position: absolute
        left: 0
        right: 0
        bottom: 0
        text-align: center
        height: .44rem
        line-height: .44rem
        color: $txColor
        ellipsis()

</style>
