<template>
  <div>
    <nav-bar>
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banner="banner"></home-swiper>
  </div>
</template>

<script>
  import NavBar from 'components/common/navbar/NavBar'
  import HomeSwiper from "./childComp/HomeSwiper"

  import {getHomeMultidata} from "network/home"

  export default {
    name: "Home.vue",
    components:{
      NavBar,
      HomeSwiper
    },
    data(){
      return {
        banner:[]
      }
    },
    methods:{
      getHomeMultidata(){
        getHomeMultidata().then(res=>{
          this.banner = res.data.banner.list
        })
      }
    },
    created(){
      this.getHomeMultidata()
    }
  }
</script>

<style scoped>

</style>
