<template>
  <div class="main">
    <index-header></index-header>
    <index-swiper :list="banner"></index-swiper>
    <index-icon :list="iconList"></index-icon>
    <index-scroll :list="sightsList"></index-scroll>
  </div>
</template>

<script>
import IndexHeader from './header'
import IndexSwiper from './swiper'
import IndexIcon from './icon'
import IndexScroll from './scroll'
import axios from 'axios'
import {mapState, mapMutations} from 'vuex'

export default {
  name: 'index',
  components: {
    IndexHeader,
    IndexSwiper,
    IndexIcon,
    IndexScroll
  },
  computed: {
    ...mapState(['city'])
  },
  data () {
    return {
      banner: [],
      iconList: [],
      sightsList: []
    }
  },
  methods: {
    ...mapMutations(['changeCity']),
    getIndexData () {
      axios.get('/api/index.json?city=' + this.city)
        .then(this.handleDataSucc.bind(this))
        .catch(this.handleDataErro.bind(this))
    },
    handleDataSucc (res) {
      res = res ? res.data : null
      if (res && res.ret && res.data) {
        res.data.city && (this.changeCity(res.data.city))
        res.data.banner && (this.banner = res.data.banner)
        res.data.iconList && (this.iconList = res.data.iconList)
        res.data.sightsList && (this.sightsList = res.data.sightsList)
      } else {
        this.handleDataErro()
      }
    },
    handleDataErro () {
      console.log('false')
    }
  },
  created () {
    this.getIndexData()
  }
}
</script>

<style lang="stylus" scoped>
</style>
