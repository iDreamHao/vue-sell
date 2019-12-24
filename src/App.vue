<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <div class="tab border-1px">
      <div class="tab-item">
        <router-link to="/goods">商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评论</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>
    <keep-alive>
      <router-view :seller="seller" ></router-view>
    </keep-alive>
  </div>
</template>

<script>
import Header from './components/header/header'
import axios from 'axios'
const ERR_OK = 0
export default {
  name: 'App',
  data () {
    return {
      seller: {}
    }
  },
  components: {
    'v-header': Header
  },
  mounted () {
    this.getHeaderData()
  },
  methods: {
    getHeaderData () {
      axios.get('/api/seller')
        .then((res) => {
          if (res.data.errno === ERR_OK) {
            this.seller = res.data.data
          }
        })
    }
  }
}
</script>

<style lang="stylus" scoped>
@import "./common/stylus/mixin.styl"
  #app
    .tab
     display:flex
     width:100%
     height:40px
     line-height 40px
     border-1px(rgba(7,17,27,0.1))
     .tab-item
       flex:1
       text-align center
       & > a
         display block
         fonr-size 14px
         color rgb(77,85,93)
         &.active
           color rgb(240,20,20)
</style>
