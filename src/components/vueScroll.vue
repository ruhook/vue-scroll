<template>
  <vue-scroll
    ref="scroll"
    :data="list"
    :pullDownRefresh="aa"
    :pullUpLoad="true"
    @pullingDown="onPullingDown"
    @pullingUp="onPullingUp"
  >
    <div class="list-warp">
      <div class="item" v-for="(item, index) in list" :key="index">{{index}}</div>
    </div>
  </vue-scroll>
</template>

<script>
import VueScroll from '../common/VueScroll'
export default {
  data () {
    return {
      list: Array(20),
      isPullup: true,
      pullup: true,
      aa: {
        threshold: 90,
        stop: 40
      }
    }
  },
  methods: {
    onPullingDown () {
      setTimeout(() => {
        this.$refs.scroll.forceUpdate()
      }, 2000)
    },
    onPullingUp () {
      setTimeout(() => {
        if (Math.random() > 0.5)        {
          console.log('push')
          this.list.push(1)
        } else        {
          // 如果没有新数据
          this.$refs.scroll.forceUpdate(false)
        }
      }, 1500)
    },
  },
  components: { VueScroll }
}
</script>

<style scoped type='text/css'>
.list-warp{
  
}
.item {
  font-size: 16px;
  height: 40px;
  line-height: 40px;
  border-bottom:1px solid #dedede;
}
</style>
