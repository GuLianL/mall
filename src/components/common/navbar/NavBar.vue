<template>
  <div class="nav-bar">
    <div class="nav-bar-left">
      <slot name="left"></slot>
    </div>
    <div class="nav-bar-center">
      <slot name="center"></slot>
    </div>
    <div class="nav-bar-right">
      <slot name="right"></slot>
    </div>
  </div>
</template>

<script>
  export default {
    name: "NavBar"
  }
</script>

<style scoped>
  .nav-bar{
    display: flex;
    height: 44px;
    line-height: 44px;
    color: #fff;
    background: var(--color-tint);
    text-align: center;
  }
  .nav-bar-left,.nav-bar-right{
    width: 60px;
  }
  .nav-bar-center{
    flex: 1;
  }
</style>
