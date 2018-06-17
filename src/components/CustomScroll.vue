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
  data () {
    return {
      barHeight: 0,
      barPosition: 0,
      barStyle: {},

      systemScrollbarWidth: 1,
      scrollerStyle: {}
    }
  },
  mounted () {
    this.$refs.content.style.height = 0
    this.updateScroller()
    this.$refs.content.style.height = 'auto'
    this.updateBar()
  },
  updated () {
    this.updateBar()
    this.updateScroller()
  },
  methods: {
    moveBar () {
      this.updateBarPosition()
      this.updateBarStyle()
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

      this.systemScrollbarWidth = this.$refs.scroller.offsetWidth - this.$refs.scroller.clientWidth
      if (oldSystemScrollbarWidth !== this.systemScrollbarWidth) {
        this.updateScrollerStyle()
      }
    },
    updateScrollerStyle () {
      let wrapperHeight = this.$refs.wrapper.clientHeight
      if (wrapperHeight < 10) {
        wrapperHeight = 'auto'
      }
      wrapperHeight += 'px'
      this.scrollerStyle = {
        'width': (this.$refs.scroller.offsetWidth + this.systemScrollbarWidth) + 'px',
        'height': wrapperHeight
      }
    },
    updateBarStyle () {
      this.barStyle = {
        'height': this.barHeight + 'px',
        'transform': 'translateY(' + this.barPosition + 'px)'
      }
    },
    updateBarHeight () {
      this.barHeight = this.$refs.wrapper.clientHeight / this.$refs.scroller.scrollHeight * this.$refs.wrapper.clientHeight
    },
    updateBarPosition () {
      let position = this.$refs.scroller.scrollTop
      this.barPosition = this.$refs.wrapper.clientHeight / this.$refs.scroller.scrollHeight * position
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
    display: flex;
    flex-wrap: wrap;
  }

  @media  (min-width: 0) and (max-width: 487px) {
    .customScroll__scrollbar {
      display: none;
    }
    .customScroll__content {
      flex-direction: column;
    }
  }
</style>
