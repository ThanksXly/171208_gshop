<template>
    <div>
      <ShopHeader/>
        <div class="tab">
          <div class="tab-item">
            <router-link to="/shop/shopgoods" replace>点餐</router-link>
          </div>
          <div class="tab-item">
            <router-link to="/shop/shopratings" replace>评价</router-link>
          </div>
          <div class="tab-item">
            <router-link to="/shop/shopinfo" replace>商家</router-link>
          </div>
        </div>
      <keep-alive>
        <router-view/>
      </keep-alive>
    </div>
</template>
<!--http://cangdu.org:8001/img/16018a5c08533.jpeg-->
<script>
  import ShopHeader from '../../components/ShopHeader/ShopHeader.vue'
  export default {
    mounted(){
      this.$store.dispatch('getShopInfo')
      this.$store.dispatch('getShopGoods')
      this.$store.dispatch('getShopRatings')
    },
    components:{
      ShopHeader
    }
  }

</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/mixins.styl"
  .tab
    height 40px
    line-height 40px
    background #fff
    bottom-border-1px(rgba(7, 17, 27, 0.1))
    .tab-item
      float left
      width: 33.3333%
      text-align center
      font-size 14px
      color rgb(77, 85, 93)
      a
        display block
        position relative
        &.router-link-active
          color #02a774
          &::after
            content ''
            position absolute
            left 50%
            bottom 1px
            width 35px
            height 2px
            transform translateX(-50%)
            background #02a774

</style>
