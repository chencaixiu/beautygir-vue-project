<template>
  <div class="main">
    <city-header></city-header>
    <city-search></city-search>
    <city-list class="list"
               :list="city"
               :hotcityList="hotcityList">
    </city-list>
  </div>
</template>

<script>
import CityHeader from './header'
import CitySearch from './search'
import CityList from './list'
import axios from 'axios'
export default {
  name: 'city',
  data () {
    return {
      city: [],
      hotcityList: []
    }
  },
  components: {
    CityHeader,
    CitySearch,
    CityList
  },
  methods: {
    getListInfo () {
      axios.get('/api/city.json')
        .then(this.handleListSucc.bind(this))
        .catch(this.handleGetListErr.bind(this))
    },
    handleListSucc (res) {
      console.log(res)
      res && (res = res.data)
      if (res && res.data) {
        res.data.city && (this.city = res.data.city)
        res.data.hotcityList && (this.hotcityList = res.data.hotcityList)
      } else {
        this.handleGetListErr()
      }
    },
    handleGetListErr () {
      console.log('erro')
    }
  },
  created () {
    this.getListInfo()
  }
}
</script>

<style lang="stylus" scoped>
  .main
    display: flex
    flex-direction: column
    position: absolute
    left: 0
    right: 0
    top: 0
    bottom: 0
    .list
      flex: 1
      overflow: hidden
</style>
