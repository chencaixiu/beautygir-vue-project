<template>
  <div>
     <div class="icons">
       <swiper :options="swiperOption">
        <swiper-slide v-for="(page,index) of pageList" :key="index">
          <div class="area-icon">
            <div class="area-item" v-for="item in page"
                                   :key="item.id">
                <img class="area-img" :src="item.imgUrl"/>
              <p class="area-descr">{{item.title}}</p>
            </div>
          </div>
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
    <div class="message">
      <div class="message1 border-right iconfont">&#xe611;<span>定位失败</span></div>
      <div class="message1 iconfont">&#xe709;<span>5折泡温泉</span></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'index-icons',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination'
      }
    }
  },
  computed: {
    pageList () {
      const pages = []
      this.list.forEach((value, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(value)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  .icons
    height: 3.8rem
    .area-icon
      display: flex
      flex-wrap: wrap
      .area-item
        width: 25%
        height: 1.9rem
        .area-img
          display: block
          margin: .3rem auto .2rem auto
          width: .66rem
          height:.66rem
        .area-descr
          white-space: nowrap
          text-overflow: ellipsis
          line-height:.4rem
          text-align: center
          font-size: .28rem
          font-weight: bold
     .swiper-pagination
        bottom: .02rem
  .message
    display: flex
    margin-top: .67rem
    height:.97rem
    align-items: center
    text-align: center
    .message1
      flex: 1
      line-height: .97rem
      span
        margin-left: .11rem
</style>
