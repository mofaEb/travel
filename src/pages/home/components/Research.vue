<template>
  <div >
    <div class="title">旅行攻略</div>
    <div class="item-wrapper">
      <div class='item' v-for="item of itemList" :key='item.id'>
        <img class='itemImg' :src="item.imgUrl" />
        <div class='itemDesc'>{{ item.desc }}</div>
      </div>
      <div class='item'></div>
      <div class='item'></div>
      <div class='item'></div>
      <div class='item'></div>

    </div>
  </div>

</template>

<script>
export default {
  name: 'HomeResearch',
  data () {
    return {
      itemList: [
        {
          id: '0001',
          imgUrl: '//tr-osdcp.qunarzz.com/tr-osd-tr-manager/img/6ff48e0e00432f823bf593deec6d3397.jpg',
          desc: '美帝的美，留在图里也要藏在心底'
        }, {
          id: '0002',
          imgUrl: '//tr-osdcp.qunarzz.com/tr-osd-tr-manager/img/729fced755d522ccfc280ef155f45518.jpg',
          desc: '在秘密花园，领略意大利风情'
        }, {
          id: '0003',
          imgUrl: '//tr-osdcp.qunarzz.com/tr-osd-tr-manager/img/e86b37fef48851353d6f5ae0090cc974.jpg',
          desc: '带着相机去旅行，圆一场青海梦'
        }, {
          id: '0004',
          imgUrl: '//tr-osdcp.qunarzz.com/tr-osd-tr-manager/img/24d074328b5a26845ebb92be20b38754.jpg',
          desc: '陪你去三亚，陪你去天涯海角'
        }
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
  .title
    line-height: .8rem
    background: #eee
    text-indent: .2rem
  .item-wrapper
    .item
      overflow: hidden
      float: left
      height: 0
      width: 47%
      padding: .1rem .1rem 42.5% .1rem
      // background #aaa
      .itemImg
        width: 100%
        border-radius: .2rem
      .itemDesc
        padding: .1rem
        font-size: .3rem
        line-height: .4rem


</style>
