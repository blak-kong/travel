<template>
  <div class="list" ref="wrapper">
      <!-- better-scroll使用格式，外面一层（滑动区域），里面一层（包裹住内容） -->
      <div>
        <div class="area">
            <div class="title border-topbottom">当前城市</div>
            <div class="button-list">
                <div class="button-wrapper">
                    <div class="button">北京</div>
                </div>
                <div class="button-wrapper">
                    <div class="button">北京</div>
                </div>
                <div class="button-wrapper">
                    <div class="button">北京</div>
                </div>
            </div>
        </div>
        <div class="area">
            <div class="title border-topbottom">热门城市</div>
            <div class="button-list">
                <div class="button-wrapper"
                v-for="item of hot"
                :key="item.id">
                    <div class="button">{{item.name}}</div>
                </div>
            </div>
        </div>
        <div class="area" v-for="(item, key) of cities" :key="key">
            <div class="title border-topbottom">{{key}}</div>
            <div class="item-list">
                <div class="item border-bottom"
                v-for="innerItem of item"
                :key="innerItem.id"
                >
                {{innerItem.name}}
                </div>
            </div>
        </div>
      </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'

export default {
  name: 'CityList',
  props: {
    hot: Array,
    cities: Object
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.border-topbottom
    &:before
        border-color #ccc
    &:after
        border-color #ccc
.border-bottom
    &:before
        border-color #ccc
.list
    overflow hidden /*超出屏幕范围则隐藏*/
    position absolute
    top 1.58rem
    left 0
    right 0
    bottom 0
    .title
        line-height .44rem
        background #eeeeee
        padding-left .2rem
        color #666666
        font-size .26rem
    .button-list
        overflow hidden /*下一级浮动，这里触发BFC*/
        padding .1rem .6rem .1rem .1rem
        .button-wrapper
            float left
            width 33.33%
            .button
                margin .1rem
                padding: .1rem 0
                text-align center
                border .02rem solid #ccc
                border-radius .06rem
    .item-list
        .item
            line-height .76rem
            padding-left .2rem
</style>
