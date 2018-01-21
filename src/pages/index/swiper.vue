<template>
  <swiper class="banner" :options="swiperOption" v-if="hasSwiper">
    <swiper-slide v-for="item of list" :key="item.id" >
      <img class="banner-img" :src="item.imgUrl" alt="">
    </swiper-slide>
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
</template>

<script>
export default {
  name: 'index-swiper',
  props: ['list'],
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        autoplay: 3000
      }
    }
  },
  computed: {
    hasSwiper () {
      return !!this.list.length
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '../../assets/stylus/varibles.style'
  .swiper-pagination >>> .swiper-pagination-bullet-active
    background: #fff
  .banner
    overflow: hidden
    height: 0
    padding-bottom: 31.25%
    .banner-img
      width: 100%
</style>
