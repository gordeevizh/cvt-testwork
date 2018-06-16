<template>
  <div class="customScroll" ref="wrapper">
    <div
      class="customScroll__scroller"
      ref="scroller"
      :style="scrollerStyle"
      @scroll="moveBar()"
    >
      <div class="customScroll__content" ref="content">
        <slot></slot>
      </div>
    </div>
    <div class="customScroll__scrollbar" ref="scrollbar">
      <div
        class="customScroll__bar"
        :style="barStyle"
      ></div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'CustomScroll',
  props: {
    containerHeight: {
      default: 0,
      type: Number
    }
  },
  data () {
    return {
      barHeight: 0,
      barPosition: 0,
      barStyle: {},

      maxScrollHight: 0,

      systemScrollbarWidth: 0,
      scrollerWidth: 0,
      scrollerStyle: {}
    }
  },
  updated () {
    this.updateMaxScrollHight()
    this.updateBar()
    this.updateScroller()
  },
  mounted () {
    this.updateBar()
  },
  methods: {
    moveBar () {
      this.updateBarPosition()

      this.barStyle = {
        'height': this.barHeight + 'px',
        'transform': 'translateY(' + this.barPosition + 'px)'
      }
    },
    updateBar () {
      let oldBarHeight = this.barHeight

      this.updateBarHeight()
      if (oldBarHeight !== this.barHeight) {
        this.updateBarStyle()
      }
    },
    updateScroller () {
      let oldSystemScrollbarWidth = this.systemScrollbarWidth

      this.scrollerWidth = this.$refs.scroller.offsetWidth
      this.systemScrollbarWidth = this.scrollerWidth - this.$refs.scroller.clientWidth
      if (oldSystemScrollbarWidth !== this.systemScrollbarWidth) {
        this.updateScrollerStyle()
      }
    },
    updateScrollerStyle () {
      this.scrollerStyle = {
        'width': (this.scrollerWidth + this.systemScrollbarWidth) + 'px',
        'height': this.containerHeight + 'px'
      }
    },
    updateBarStyle () {
      this.barStyle = {
        'height': this.barHeight + 'px',
        'transform': 'translateY(' + this.barPosition + 'px)'
      }
    },
    updateBarHeight () {
      this.barHeight = this.containerHeight / this.maxScrollHight * this.containerHeight
    },
    updateBarPosition () {
      let position = this.$refs.scroller.scrollTop
      this.barPosition = (this.containerHeight - this.barHeight) / this.maxScrollHight * position
    },
    updateMaxScrollHight () {
      this.maxScrollHight = this.$refs.scroller.scrollHeight - this.containerHeight
    }
  }
}
</script>

<style scoped>
  .customScroll {
    overflow: hidden;
    position: relative;
    width: 100%;
  }
  .customScroll__scroller {
    overflow-y: scroll;
    padding: 0;
    border: none;
  }
  .customScroll__scroller::-webkit-scrollbar {
    width: 0;
  }
  .customScroll__scrollbar {
    width: 5px;
    height: 100%;
    background: #ededed;
    position: absolute;
    top: 0;
    right: 0;
    border-radius: 3px;
  }
  .customScroll__bar {
    width: 100%;
    background: #0f7bb1;
    border-radius: 3px;
  }
  .customScroll__content {
  }
</style>
