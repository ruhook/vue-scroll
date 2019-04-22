<template>
  <vue-scroll
    ref="scroll"
    :data="list"
    :pullDownRefresh="pullDownRefresh"
    :pullUpLoad="pullUpLoad"
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
      pullUpLoad: true,    // 开启上拉加载的条件
      pullDownRefresh: 40  // 开启下拉刷新&&触发刷新条件的高度
    }
  },
  methods: {
    onPullingDown () {
      setTimeout(() => {
        this.$refs.scroll.forceUpdate()
      }, 2000)
    },
    onPullingUp () {
      if (this.list.length >= 21)      {
        this.$refs.scroll.forceUpdate(false)
        return
      }
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
