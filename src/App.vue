<template>
  <div id="app" >
      <v-header></v-header>
    <div class="tab">
    <div class="tab-item">
      <a >商品</a>
      </div>
      <div class="tab-item">
         <a >评论</a>
      </div>
      <div class="tab-item">
        <a >商家</a>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/header/header'
export default {
  name: 'App',
  components: {
    'v-header': Header
  }
}
</script>

<style lang="stylus" scoped>
  #app
    .tab
     display:flex
     width:100%
     height:40px
     line-height 40px
     .tab-item
       flex:1
       text-align center
</style>
