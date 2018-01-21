<template>
  <div class="hotsale-container">
    <div class="hotsale-title">
      <h2 class="hotsale-introduce">热销推荐</h2>
    </div>
    <div class="sights-container">
      <router-link to="/detail">
      <div class="sights-items" v-for="item of list" :key="item.id">
          <img class="sights-img" v-lazy="item.imgUrl" alt="">
        <ul class="sights-message">
          <h3 class="sights">{{item.title}}</h3>
          <p class="sights-introduce">{{item.introduce}}</p>
          <p class="price">
            <span class="mark">￥</span>
            <em class="money">{{item.money}}</em>
            <i class="word">起</i>
          </p>
        </ul>
      </div>
      </router-link>
      <div class="all-sights">查看所有产品</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'index-hotsale',
  props: ['list']
}
</script>

<style lang="stylus" scoped>
  .hotsale-container
    .hotsale-title
      height:.8rem
      .hotsale-introduce
        padding-left: .13rem
        background: #f5f5f5
        font-size: .28rem
        line-height: .8rem
    .sights-items
      display: flex
      padding-top: .24rem
      padding-left: .24rem
      padding-bottom: .22rem
      border-bottom: .02rem solid #f5f5f5
      .sights-img
        margin-right: .2rem
        height: 1.4rem
        width: 1.4rem
      .sights-message
        float: right
        .sights-introduce
          margin-top: .2rem
          margin-bottom: .24rem
          font-size: .28rem
          color: #9e9e9e
        .sights
         font-size: .28rem
         color: #212121
        .mark
          font-size: .18rem
          color: #ff8300
        .money
          font-size: .32rem
          font-size: blod
          color: #ff8300
        .word
          font-size: .28rem
          color: #9e9e9e
    .all-sights
      height: .86rem
      line-height: .86rem
      text-align: center
      font-size: .28rem
      font-size: blod
      color: #00afc7
</style>
