<template>
  <div class="header">
    <div class="back iconfont">&#xe679;</div>
    <div class="search iconfont">
      <span>&#xe615;</span>
      输入城市/景点/游玩主题
    </div>
    <router-link to="/city">
      <div class="city">
        北京
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'index-header'
}
</script>

<style lang="stylus" scoped>
@import "../../assets/stylus/varibles.style";
  .header
    display: flex
    height: .88rem
    line-height: .88rem
    background: $bgColor
    .back
      width: .58rem
      text-align: center
      font-size: .5rem
      font-weight: bold
      color: #fff
    .search
      flex: 1
      height: .6rem
      line-height: .6rem
      margin: .14rem .2rem
      padding-left: .4rem
      background: #fff
      border-radius: .1rem
      font-size: .28rem
      font-weight: bold
      color: #ccc
    .city
      position: relative
      padding-right: .6rem
      color: #fff
      &:before
        position: absolute
        top: .36rem
        right: .26rem
        content: "\0020"
        width: 0
        height: 0
        border-left: .14rem solid transparent
        border-right: .14rem solid transparent
        border-top: .14rem solid #fff
</style>
