
<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xeb99;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xeb9c;</span>
      输入城市/景点/游玩主题</div>
      <router-link to="./city">
      `<div class="header-right">
        {{this.city}}
        <span class="iconfont arrow-icon">&#xe62d;</span>
      </div>`
      </router-link>
  </div>
</template>

<script>

import {mapState} from 'vuex'

export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style >

.header {
  display: flex;
  line-height: 0.86rem;
  background: #00bcd4;
  color: #fff;
}
.header.header-left{
  width: .64rem;
  float: left;
}
.header .header-left .back-icon{
  margin-left: .1rem;
  text-align: center;
  font-size: .4rem;
}
.header .header-input{
  flex: 1;
  height: .64rem;
  line-height: .64rem;
  margin-top: .12rem;
  margin-left: .2rem;
  background: #fff;
  padding-left: .2rem;
  border-radius:.1rem;
  color: #ccc;
}
.header .header-right{
  min-width: 1.04rem;
  padding: .1rem;
  float: right;
  text-align: center;
  color: #fff;
}
.header .header-right.arrow-icon{
  font-size: .2rem;
}

</style>
