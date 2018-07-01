<template>
  <ul class="list">
      <li class="item"
      v-for="item of letters"
      :key="item"
      :ref="item"
      @click="handleLetterClick"
      @touchstart="handleTouchStart"
      @touchmove="handleTouchMove"
      @touchend="handleTouchEnd">
          {{item}}
      </li>
  </ul>
</template>

<script>

export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  data () {
    return {
      touchStatus: false, // 标识位
      startY: 0,
      timer: null
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  },
  methods: {
    handleLetterClick (e) { // 向外触发事件
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart () { // 拖动开始
      this.touchStatus = true
    },
    handleTouchMove (e) { // 拖动中
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.time)
        }
        this.timer = setTimeout(() => { // 节流
        // 插件需要获取dom,然后计算高度。
          const touchY = e.touches[0].clientY - 79 // 移动端touch事件,减去header的高
          const index = Math.floor((touchY - this.startY) / 20)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handleTouchEnd () { // 拖动结束
      this.touchStatus = false
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
 .list
     display flex
     flex-direction column
     justify-content center
     position absolute
     top 1.58rem
     right 0
     bottom 0
     width .4rem
     .item
         line-height .44rem
         text-align center
         color $bgColor
</style>
