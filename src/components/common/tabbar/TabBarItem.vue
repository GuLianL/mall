<template>
  <div class="tabbar-item" @click="itemClick">
    <slot name="icon" v-if="!isActive"></slot>
    <slot name="active_icon" v-else></slot>
    <div :style="activeStyle">
      <slot name="text"></slot>
    </div>
  </div>
</template>

<script>
  export default {
    name: "TabBarItem.vue",
    props:{
      path: String,
      activeColor: {
        type: String,
        default: 'red'
      }
    },
    data(){
      return {
        currentIndex: 0
      }
    },
    methods:{
      itemClick(){
        console.log(this.$route.path.indexOf(this.path))
        this.$router.replace(this.path).catch(()=>{
        })
      }
    },
    computed:{
      isActive(){
        return this.$route.path.indexOf(this.path) !== -1
      },
      activeStyle(){
        return this.isActive ? {color: this.activeColor}: ""
      }
    }
  }
</script>

<style scoped>
  .tabbar-item{
    flex: 1;
    font-size: 14px;
    text-align: center;
  }
  .tabbar-item img{
    width: 22px;
    height: 22px;
    margin-top: 6px;
    margin-bottom: 3px;
    vertical-align: middle;
  }
</style>
