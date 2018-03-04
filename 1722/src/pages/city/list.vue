<template>
  <div class="list">
    <div class="area">
      <div class="title border-topbottom">当前位置</div>
      <div class="content">
        <div class="button">北京</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'city-list',
  props: {
    list: Object,
    hotCity: Array
  },
  watch: {
    list () {
      console.log(this.list)
    }
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
</style>
