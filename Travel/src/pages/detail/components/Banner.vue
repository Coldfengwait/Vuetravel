<template>
<div>
  <div class="banner" @click="handleBannerClick">
  <img class="banner-img" :src="bannerImg">
  <div class="banner-info">
    <div class="banner-tittle">{{this.sightName}}</div>
    <div class="banner-number"><span class="iconfont banner-icon">&#xe67f;</span>{{this.bannerImgs.length}}</div>
    </div>
  </div>
  <FadeAnimation>
    <CommonGallary :imgs="bannerImgs" v-show="showGallary" @close="handleBannerClose"></CommonGallary>
  </FadeAnimation>
</div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'
export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  },
  data () {
    return {
      showGallary: false
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    handleBannerClose () {
      this.showGallary = false
    }
  },
  components: {
    CommonGallary,
    FadeAnimation
  }
}
</script>
<style>
.banner{
  position: relative;
  overflow: hidden;
  height: 0;
  padding-bottom: 55%;
}
.banner .banner-img{
  width: 100%;
}
.banner .banner-info{
  display: flex;
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  line-height: .6rem;
  color: #fff;
  background-image: linear-gradient(top,rgba(0,0,0,0), rgba(0,0,0,0.8))
}
.banner .banner-info .banner-tittle{
  font-size: .32rem;
  padding: 0 .2rem;
  flex: 1;
}
.banner .banner-info .banner-number{
  padding: 0 .4rem;
  line-height: .4rem;
  height: .42rem;
  margin-top: 0 .14rem;
  font-size: .24rem;
  border-radius: .2rem;
  background: rgba(0, 0, 0, .8)
}
.banner .banner-info .banner-number .banner-icon{
  font-size: .24rem;
}
</style>
