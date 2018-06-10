<template>
  <div class="wrapper">
    <swiper :options="swiperOption" ref="mySwiper" @someSwiperEvent="callback">
    <!-- slides -->
      <swiper-slide v-for="item of swiperList" :key="item.id">
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
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination', //下标点
        loop: true // 轮播
      },
      swiperList: [{
        id: '001',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1805/3b/ef86879aa50e3002.jpg_750x200_2a108508.jpg'
      }, {
        id: '002',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1805/e5/59fad13a64807d02.jpg_750x200_713ae984.jpg'
      }, {
        id: '003',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1805/13/6332699c44387902.jpg_750x200_b7afa4f8.jpg'
      }]
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
