<template>
  <div class="main">
    <index-header></index-header>
    <index-swiper :list="swiperList"></index-swiper>
    <index-icons :list="iconList"></index-icons>
    <index-scroller :list="sightsList"></index-scroller>
  </div>
</template>

<script>
import IndexHeader from './header'
import IndexSwiper from './swiper'
import IndexIcons from './icons'
import IndexScroller from './scroller'
import axios from 'axios'
export default {
  name: 'index',
  components: {
    IndexHeader,
    IndexSwiper,
    IndexIcons,
    IndexScroller
  },
  data () {
    return {
      swiperList: [],
      iconList: [],
      sightsList: []
    }
  },
  methods: {
    getIndexData () {
      axios.get('api/index.json?city=' + this.$store.state.city)
        .then(this.handleGetDataSucc.bind(this))
        .catch(this.handleErro.bind(this))
    },
    handleGetDataSucc (res) {
      const data = res.data.data
      this.swiperList = data.swiperList
      this.iconList = data.iconList
      this.sightsList = data.sightsList
      if (!this.$store.state.city) {
        // this.$store.commit('changeCity', data.city)
        this.$store.dispatch('DelayThirdSeconds', data.city)
      }
    },
    handleErro () {
      console.log(false)
    }
  },
  created () {
    this.getIndexData()
  }
}
</script>

<style lang="stylus" scoped>
  .main
    display: flex
    flex-direction: column
    position: absolute
    top: 0
    left: 0
    right: 0
    bottom: 0
</style>
