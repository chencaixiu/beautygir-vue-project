<template>
  <div class="list">
    <div class="area">
      <div class="title border-topbottom">当前位置</div>
      <div class="content">
        <div class="button">
          <div class="button-text button-active">
            {{city || "北京"}}
          </div>
        </div>
      </div>
    </div>
    <div class="area">
      <div class="title border-topbottom">热门城市</div>
      <div class="content">
        <div class="button" v-for="item of hotcityList" :key="item.id">
          <div class="button-text"
               :class="{'button-active': item.name === city }">
            {{item.name}}
          </div>
        </div>
      </div>
    </div>
    <div class="area" v-for="(item,index) of list" :key="index">
      <div class="title border-topbottom">
        {{item.classify}}
      </div>
      <div class="content">
        <div class="button"
             v-for="cityItem of item.cityList"
             :key="cityItem.id">
          <div class="button-text">
            {{cityItem.name}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import {mapState} from 'vuex'
import Bscroll from 'better-scroll'
export default {
  name: 'city-list',
  props: {
    list: Array,
    hotcityList: Array
  },
  computed: {
    ...mapState(['city'])
  },
  watch: {
    city () {
      console.log(this.city)
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '../../assets/stylus/varibles.style'
  .area
    .title
      line-height: .54rem
      padding-left: .3rem
      background: #eee
      color: #616161
      font-size: .26rem
      &::before,&::after
        border-color: #919191
    .content
      overflow: hidden
      padding: 0 .4rem 0 .2rem
      .button
        float: left
        width: 33.33%
        .button-text
         height: .6rem
         line-height: .6rem
         overflow: hidden
         margin: .2rem
         border: .02rem solid #999
         border-radius: .1rem
         text-align: center
        .button-active
          color: $bgColor
          border-color: $bgColor
 </style>
