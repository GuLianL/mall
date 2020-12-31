<template>
  <div id="hy-swiper">
    <div class="swiper" @touchstart="touchstart" @touchmove="touchmove" @touchend="touchend">
      <slot></slot>
    </div>
    <slot name="indicator"></slot>
    <div class="indicator">
      <slot name="indicator" v-if="showIndicator && slideCount>1">
        <div v-for="(item, index) in slideCount"
             class="indi-item"
             :class="{active: index===currentIndex-1}"
              :key="index"></div>
      </slot>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Swiper",
    data(){
      return {
        slideCount: [],
        showIndicator: false
      }
    },
    methods:{
      touchstart(){
        console.log('touchstart')
      },
      touchmove(){
        console.log('touchmove')
      },
      touchend(){
        console.log('touchend')
      }
    }
  }
</script>

<style scoped>
  #hy-swiper {
    overflow: hidden;
    position: relative;
  }

  .swiper {
    display: flex;
  }

  .indicator {
    display: flex;
    justify-content: center;
    position: absolute;
    width: 100%;
    bottom: 8px;
  }

  .indi-item {
    box-sizing: border-box;
    width: 8px;
    height: 8px;
    border-radius: 4px;
    background-color: #fff;
    line-height: 8px;
    text-align: center;
    font-size: 12px;
    margin: 0 5px;
  }

  .indi-item.active {
    background-color: rgba(212,62,46,1.0);
  }
</style>
