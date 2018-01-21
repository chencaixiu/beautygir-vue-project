<template>
  <div class="header">
    <div class="header-icon iconfont">&#xe606;</div>
    <div class="header-search">
      <div class="headersearch-content">
        <span class="iconfont search-icon">&#xe7d4;</span>
        请输入城市/景点/游玩主题
      </div>
    </div>
    <router-link to="/city">
     <div class="header-city">{{city}}</div>
    </router-link>
  </div>
</template>

<script>
import {mapState} from 'vuex'
export default {
  name: 'index-header',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style lang="stylus" scoped>
  @import '../../assets/stylus/varibles.style'
  .header
    display: flex
    height: .88rem
    background: $bgColor
    .header-icon
      width: .88rem
      line-height: .88rem
      text-align: center
      font-size: .44rem
      font-weight: bold
      color: #fff
  .header-search
    flex: 1
    .headersearch-content
      width: 100%
      line-height: .6rem
      margin-top: .14rem
      border-radius: .1rem
      text-indent: .2rem
      background: #fff
      color: #ccc
      .search-icon
        position: relative
        top: .02rem
  .header-city
    position: relative
    float: right
    max-width: 1.6rem
    white-space: nowrap
    overflow: hidden
    text-overflow: ellipsis
    padding: 0 .46rem 0 .2rem
    line-height: .88rem
    font-size: .28rem
    color: #fff
    &::before
      position: absolute
      top: .35rem
      right: .16rem
      content: ""
      width: 0
      height: 0
      border-left: .14rem solid transparent
      border-right: .14rem solid transparent
      border-top: .14rem solid #fff
</style>
