<template>
  <div ref="wrapper">
    <div class="list">
      <div class="area">
        <div class="title border-topbottom">当前位置</div>
        <div class="content">
          <div class="button">
            <div class="button-text button-active">{{$store.state.city}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="content">
          <div class="button" v-for="item of hotCity" :key="item.id">
            <div class="button-text"
                 @click="handleClick">
              {{item.city}}
            </div>
            <!-- :class="{'button-active': item.city === city}" -->
          </div>
        </div>
      </div>
      <div class="area" v-for="(item, key) of list" :key="key">
        <div class="title border-topbottom">{{key}}</div>
        <div class="content" v-for="innerItem of item" :key="innerItem.id">
          <div class="content-item border-bottom">
            {{innerItem.name}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BSscroll from 'better-scroll'
export default {
  name: 'city-list',
  props: {
    list: Object,
    hotCity: Array
  },
  watch: {
    list () {
      this.$nextTick(() => {
        this.scroll.refresh()
      })
    }
  },
  methods: {
    handleClick (e) {
      this.$store.commit('changeCity', e.target.innerHTML)
      this.$router.go(-1)
    }
  },
  mounted () {
    this.scroll = new BSscroll(this.$refs.wrapper, {
      scrollY: true
    })
  }
}
</script>

<style lang="stylus" scoped>
  .area
    .title
       line-height: .54rem;
       padding-left: .3rem;
       background: #eee;
       color: #616161;
       font-size: .26rem;
       &::before,&::after
        border-color: #9e9e9e
    .content
      overflow: hidden
      padding: 0 .4rem 0 0.2rem
      .button
        float: left
        width: 33.33%
        .button-text
          margin: .2rem
          border: .02rem solid #999
          border-radius: .06rem
          text-align: center
          line-height: .6rem
        .button-active
          color: #00bcd4
          border-color: #00bcd4
      .content-item
        line-height: .6rem
</style>
