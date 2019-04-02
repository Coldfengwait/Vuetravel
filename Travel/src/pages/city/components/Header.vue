<template>
  <div class="header">城市选择
    <router-link to='/'>
    <div class="iconfont header-back">&#xeb99;</div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style>
.header{
  position: relative;
    overflow: hidden;
    height: .86rem;
    line-height: .86rem;
    text-align: center;
    background:#00bcd4;
    font-size: .32rem;
    color: #fff;
}
.header .header-back{
  position: absolute;
  top: 0;
  left: 0;
  width: .64rem;
  text-align: center;
  font-size: .4rem;
  color: #fff;
}
</style>
