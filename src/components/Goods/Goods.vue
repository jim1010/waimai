<template>
  <div class="goods">

    <!--分类-->
    <div class="menu-wrapper">
      <ul>
        <li class="menu-item">
          <p class="text">
            <img :src="container.tag_icon" v-if="container.tag_icon" class="icon">
            {{container.tag_name}}
          </p>
        </li>
        <li class="menu-item" v-for="item in goods">
          <p class="text">
            <img :src="item.icon" v-if="item.icon" class="icon">
            {{item.name}}
          </p>
        </li>
      </ul>
    </div>

    <!--商品列表-->
    <div class="foods-wrapper"></div>

  </div>
</template>

<script>
  export default {
    name: "Goods",
    data() {
      return {
        container: {},
        goods: []
      }
    },
    created() { // 发起异步请求获取数据
      var that = this;
      this.$axios.get('/api/goods')
        .then(function (response) { // 返回数据处理
          // console.log(response);
          var dataSource = response.data;
          if (dataSource.code == 0) {
            that.container = dataSource.data.container_operation_source;
            that.goods = dataSource.data.food_spu_tags;
            // console.log(that.poiInfo);
          }
        })
        .catch(function (error) { // 错误处理
          console.log(error);
        });
    }
  }
</script>

<style scoped>
  @import url("Goods.css");
</style>
