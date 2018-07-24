<template>
  <div id="app">
    <!-- 头部-->
    <MyHeader></MyHeader>
    <!-- 导航-->
    <MyNav></MyNav>
    <!-- 主题-->
    <!-- 路由出口 -->
    <!-- 路由匹配到的组件将渲染在这里 -->
    <router-view></router-view>
  </div>
</template>

<script>
import MyHeader from './components/Header/Header';
import MyNav from './components/Nav/Nav';

export default {
  name: 'App',
  components: {
    MyHeader,
    MyNav
  }
}
</script>

<style>

</style>
