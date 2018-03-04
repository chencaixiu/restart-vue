<template>
  <div class="scroller" ref="scroller">
  <ul class="content">
    <router-link class="sights-box clearfix"
                 v-for="item of list"
                 :key="item.id"
                 tag="li"
                 :to="'/detail/'+item.id">
      <div class="img-box">
        <img class="sights-img" v-lazy="item.imgUrl">
      </div>
      <div class="sights-describe">
        <h3 class="sights-title">{{item.title}}</h3>
        <p class="sights-introduce">{{item.introduce}}</p>
        <div class="sights-price">
          <span>￥</span>
          <span class="price">{{item.price}}</span>
          <span class="word">起</span>
        </div>
      </div>
    </router-link>
  </ul>
</div>
</template>

<script>
import BScroll from 'better-scroll'

export default {
  name: 'index-scroller',
  props: {
    list: Array
  },
  watch: {
    list () {
      this.$nextTick(() => {
        this.scroller.refresh()
      })
    }
  },
  mounted () {
    this.scroller = new BScroll(this.$refs.scroller)
  }
}
</script>

<style lang="stylus" scoped>
  .clearfix
    overflow: hidden
  .scroller
    flex: 1
    overflow: hidden
    .sights-box
      padding: .24rem
      .img-box
        float: left
        width: 1.4rem
        height: 1.4rem
        .sights-img
          width: 100%
          height: 100%
      .sights-describe
        float: left
        margin-left: .24rem
        .sights-title
          margin-bottom: .2rem
          font-size: .3rem
          color: #212121
        .sights-introduce
          margin-bottom: .3rem
          color: #9e9e9e
        .sights-price
          color: #ff8300
          .price
            font-size: .36rem
          .word
            font-size: .24rem
            color: #9e9e9e
</style>
