<template>
  <div id="app">
    <!-- 头部-->
    <MyHeader :poiInfo="poiInfo"></MyHeader>
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
  },
  data(){
    return {
      // header组件需要的数据（商家信息）
      poiInfo: {}
    }
  },
  created(){ // 发起异步请求获取数据
    var that = this;
    this.$axios.get('/api/goods')
      .then(function (response) { // 返回数据处理
        // console.log(response);
        var dataSource = response.data;
        if (dataSource.code == 0){
          that.poiInfo = dataSource.data.poi_info;
          // console.log(that.poiInfo);
        }
      })
      .catch(function (error) { // 错误处理
        console.log(error);
      });
  }
}
</script>

<style>

</style>
