<template>
  <tab-bar>
    <tab-bar-item path="/home">
      <img slot="icon" src="~assets/img/tabbar/home.svg"/>
      <img slot="active_icon" src="~assets/img/tabbar/home_active.svg"/>
      <div slot="text">首页</div>
    </tab-bar-item>
    <tab-bar-item path="/category">
      <img slot="icon" src="~assets/img/tabbar/category.svg"/>
      <img slot="active_icon" src="~assets/img/tabbar/category_active.svg"/>
      <div slot="text">分类</div>
    </tab-bar-item>
    <tab-bar-item path="/shopcart">
      <img slot="icon" src="~assets/img/tabbar/shopcart.svg"/>
      <img slot="active_icon" src="~assets/img/tabbar/shopcart_active.svg"/>
      <div slot="text">购物车</div>
    </tab-bar-item>
    <tab-bar-item path="/profile">
      <img slot="icon" src="~assets/img/tabbar/profile.svg"/>
      <img slot="active_icon" src="~assets/img/tabbar/profile_active.svg"/>
      <div slot="text">我的</div>
    </tab-bar-item>
  </tab-bar>
</template>

<script>
  import TabBar from 'components/common/tabbar/TabBar'
  import TabBarItem from 'components/common/tabbar/TabBarItem'
  export default {
    name: "MainTabBar.vue",
    components: {
      TabBar,
      TabBarItem
    }
  }
</script>

<style scoped>

</style>
