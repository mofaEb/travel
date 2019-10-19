<template>
  <div>
    <div class="title">当季景点门票</div>
    <ul>
      <li class="item border-bottom" v-for="item of recommendList" :key='item.id'>
        <img class="item-img" :src="item.imgUrl" />
        <div class="item-info">
          <p class="item-title">{{ item.title }}</p>
          <p class="item-desc">{{ item.desc }}</p>
          <button class="item-btn">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  data () {
    return {
      recommendList: [
        {
          id: '0001',
          imgUrl: '//img1.qunarzz.com/sight/p0/1506/f6/f6b727f036fe5d6d.water.jpg_256x160_1175658b.jpg',
          title: '鼓浪屿',
          desc: '琴之岛，乐之屿'
        }, {
          id: '0002',
          imgUrl: '//img1.qunarzz.com/sight/p0/1902/91/919987896bca93ba3.img.jpg_256x160_0ce8a0d6.jpg',
          title: '厦门园林植物园',
          desc: '一座秀丽多姿、四季飘香的游览园林'
        }, {
          id: '0003',
          imgUrl: '//img1.qunarzz.com/sight/p0/201301/09/1687a8df31b0c42e93835fbb.jpg_256x160_218d8ae5.jpg',
          title: '冠豸山',
          desc: '“北夷南豸，丹霞双绝”'
        }, {
          id: '0004',
          imgUrl: '//img1.qunarzz.com/sight/p0/201311/05/5c9d25aa40ef722ec8d65eac.jpg_256x160_4f164736.jpg',
          title: '武夷山',
          desc: '满园秋色尽在武夷风光'
        }
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/mixins.styl'
  .title
    margin-top: .2rem
    line-height: .8rem
    background: #eee
    text-indent: .2rem
  .item
    overflow: hidden
    display: flex
    height: 1.9rem
    .item-img
      width: 1.7rem
      height: 1.7rem
      padding: .1rem
      overflow: hidden
    .item-info
      flex: 1
      padding: .1rem
      min-width: 0
      .item-title
        line-height: .54rem
        font-size: .32rem
      .item-desc
        line-height: .4rem
        color: #bbbbbb
        ellipsis()
      .item-btn
        line-height: .44rem
        margin-top: .16rem
        background: #ff9300
        padding: 0 0.1rem
        border-radius: .06rem
        color: #ffffff
</style>
