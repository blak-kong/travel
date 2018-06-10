<template>
  <div class="header">
    <div class="header-left">
      <span class="iconfont back-icon">
        <i class="icon-fanhui"></i>
      </span>
    </div>
    <div class="header-input">
      <span class="iconfont">
        <i class="icon-sousuo"></i>
      </span>
      输入城市/景点/游玩主题</div>
    <div class="header-right">
      城市
      <span class="iconfont arrow-icon">
        <i class="icon-jiantou"></i>
      </span>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Home'
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header
    display: flex
    line-height: .86rem
    background: $bgColor /*抽离公用样式*/
    color: #fff
    .header-left
      width: .64rem
      float: left
      display: flex
      justify-content: center
      .back-icon
        font-size: .4rem
    .header-input
      flex: 1
      height: .64rem /*86-24(margin)*/
      line-height: .64rem
      margin-top: .12rem
      margin-left: .2rem
      padding-left: .2rem
      background: #fff
      border-radius: .1rem
      color: #ccc
    .header-right
      width: 1.24rem
      float: right
      text-align: center
      .arrow-icon
        margin-left: -.04rem
        font-size: .24rem
</style>
