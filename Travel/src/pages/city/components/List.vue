<template>
  <div class="city_list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.currentCity}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper" v-for="item of hot" :key="item.id" @click="handleCityClick(item.name)">
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item,key) of cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list">
          <div class="item border-bottom" @click="handleCityClick(innerItem.name)"  v-for="innerItem of item" :key="innerItem.id">
            {{innerItem.name}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import {mapState, mapMutations} from 'vuex'
export default {
  name: 'CityList',
  props: {
    hot: Array,
    cities: Object,
    letter: String
  },
  methods: {
    handleCityClick (city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>

<style>
.city_list{
  overflow: hidden;
  position: absolute;
  top: 1.58rem;
  left: 0;
  right: 0;
  bottom: 0;
}
.city_list .border-topbottom{
  border-color: #ccc;
}
.city_list .title{
  line-height: .54rem;
  background: #eee;
  padding-left: .2rem;
  color: #666;
  font-size: .26rem;
}
.city_list .button-list{
  overflow: hidden;
  padding: .1rem .6rem .1rem .1rem;
}
.city_list .button-list .button-wrapper{
  float: left;
  width: 33.33%
}
.city_list .button-list .button-wrapper .button{
  text-align: center;
  margin: .1rem;
  border: .02rem solid #ccc;
  padding: .1rem 0;
  border-radius: .06rem;
}
.city_list .item-list .item{
  line-height: .76rem;
  padding-left: .2rem;
}
.city_list .item-list .border-bottom{
 border-color: #666;
}
</style>
