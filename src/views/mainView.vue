<template>
  <div class="fullMain">
    我是主页
    <router-link to="/mainView/echartsView">Echarts</router-link>
    <router-view></router-view>
  </div>
</template>

<script>
    export default {
        name: "mainView"
    }
</script>

<style>
  .fullMain{
    width: 100%;
    height: 100%;
    overflow: auto;
  }
</style>
