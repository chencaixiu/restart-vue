<template>
  <div class="search">
    <input type="text" class="search-input" placeholder="输入城市或拼音"/>
  </div>
</template>

<script>
export default {
  name: 'city-search'
}
</script>

<style lang="stylus" scoped>
@import "../../assets/stylus/varibles.style";
  .search
    height: .72rem
    background: $bgColor
    padding: 0 .4rem
    .search-input
      line-height: .62rem
      width: 100%
      margin-top: .02rem
      border-radius: .1rem
      text-align: center
      font-size: .24rem
      color: #666
</style>
