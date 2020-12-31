<template>
  <div id="tabbar">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: "TabBar.vue"
  }
</script>

<style scoped>
  #tabbar{
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    display: flex;

    height: 49px;
    background: #f2f2f2;
    -webkit-box-shadow: 0 1px 3px #b3b3b3;
    -moz-box-shadow: 0 1px 3px #b3b3b3;
    box-shadow: 0 1px 3px #b3b3b3;
  }
</style>
