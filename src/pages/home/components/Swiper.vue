<template>
  <div class="wrapper">
    <swiper :options="swiperOption" v-if="showSwiper">
    <!-- slides -->
      <swiper-slide v-for="item of list" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl">
      </swiper-slide>
    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>

export default {
  name: 'HomeSwiper',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination', // 下标点
        loop: true // 轮播
      }
    }
  },
  computed: {
    showSwiper () {
      return this.list.length
    }
  }
}
</script>

<style lang="stylus" scoped>
/*样式穿透scoped*/
.wrapper >>> .swiper-pagination-bullet-active
    background: #fff!important
.wrapper
  overflow: hidden
  width: 100%
  height: 0 /*高度相对宽度自动撑开31.24%*/
  padding-bottom: 26.66%
  background: #eee /*图片没显示出来时显示*/
  .swiper-img
    width: 100%
</style>
