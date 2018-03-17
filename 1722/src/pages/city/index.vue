<template>
  <div class="main">
    <city-header></city-header>
    <city-search></city-search>
    <city-list class="list"
               :hotCity="hotCity"
               :list="list">
    </city-list>
  </div>
</template>

<script>
import CityHeader from './header'
import CitySearch from './search'
import CityList from './list'
import axios from 'axios'
export default {
  name: 'city',
  data () {
    return {
      'hotCity': [],
      'list': {}
    }
  },
  components: {
    CityHeader,
    CitySearch,
    CityList
  },
  methods: {
    getListInfo () {
      axios.get('api/city.json?city=' + this.$store.state.city)
        .then(this.handleDataSucc.bind(this))
        .catch(this.handleDataErro.bind(this))
    },
    handleDataSucc (res) {
      res && (res = res.data)
      if (res && res.data) {
        res.data.hotCity && (this.hotCity = res.data.hotCity)
        res.data.list && (this.list = res.data.list)
      } else {
        this.handleDataErro()
      }
    },
    handleDataErro () {
      console.log('false')
    }
  },
  created () {
    this.getListInfo()
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
    .list
      overflow: hidden
      flex: 1
</style>
