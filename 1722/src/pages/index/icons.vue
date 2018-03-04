<template>
  <div class="icons-container clearfix">
    <swiper class="swiper-container" :options="swiperOption">
      <swiper-slide v-for="(page, index) of pageList" :key="index">
        <div class="sight-box" v-for="item of page" :key="item.id">
          <router-link to="item.link">
            <img class="sight-img" :src="item.imgUrl"/>
          </router-link>
          <p class="sights-name">{{item.title}}</p>
        </div>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'index-icons',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination'
      }
    }
  },
  computed: {
    pageList () {
      const pages = []
      this.list.forEach((value, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(value)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  .swiper-container
    padding-bottom: .6rem
    position: relative
    .sight-box
      float: left
      height: 1.6rem
      width: 1.86rem
      .sight-img
        display: block
        width: .66rem
        height: .66rem
        margin: .3rem auto .2rem
      .sights-name
        text-align: center
        font-size: .28rem
        color: #212121
    .swiper-pagination
      position: absolute
      bottom: .1rem
      left: 0
      width: 100%
</style>
