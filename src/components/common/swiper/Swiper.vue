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
    props:{
      interval:{
        type: Number,
        default: 2000
      },
      showIndicator: {
        type: Boolean,
        default: true
      },
      animDuration:{
        type: Number,
        default: 300
      }
    },
    data(){
      return {
        playTimer: null,
        slideCount: 0, //元素个数
        totalWidth: 0, // swiper的宽度
        swiperStyle: {}, //swiper样式
        currentIndex: 1, //当前的index
        scrolling: false, //是否正在滚动
      }
    },
    mounted(){
      setTimeout(()=>{
        this.handleDom()

        this.startTimer()
      }, 100)
    },
    methods:{
      startTimer(){
        this.playTimer = window.setInterval(()=>{
          this.currentIndex++
          this.scrollContent(-this.currentIndex * this.totalWidth)
        }, this.interval)
      },
      stopTimer(){
        window.clearInterval(this.playTimer)
      },
      /*
      * 滚动到正确的位置
      * */
      scrollContent(currenrPosition){
        this.setTransform(currenrPosition)
        this.checkPosition()
      },
      setTransform(position){
        this.swiperStyle.transform = `translate3d(${position}px, 0, 0)`
      },
      /*
      * 检验正确的位置
      * */
      checkPosition(){
        window.setTimeout(()=>{
          this.swiperStyle.transform = '0ms'
          console.log(this.currentIndex, this.slideCount)
          if(this.currentIndex >= this.slideCount + 1){
            this.currentIndex = 1
          }
        })
      },
      handleDom(){
        let swiperEl = document.querySelector('.swiper')
        let swiperEls = document.getElementsByClassName('slide')

        this.slideCount = swiperEls.length //滚动的总数
        this.totalWidth = swiperEl.offsetWidth //获取滚动区域的宽度
        this.swiperStyle = swiperEl.style

      },
      /*
      * 拖动事件的处理
      * */
      touchstart(){
        //1、如果正在滚动，则不可以拖动
        if(this.scrolling) return false

        //2、停止定时器
        this.stopTimer();

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
