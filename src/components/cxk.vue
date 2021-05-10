<template>
  <div :style="transStyle" v-on:click="this.clickHandler">
    <div id='tag'>{{ index }}</div>
    <img src='../assets/cxk.jpeg' />
  </div>
</template>

<script>
export default {
  name: 'cxk',
  props: {
    initAngle: {
        type: Number,
        required: true
    },
    borderWidth: Number,
    borderHeight: Number,
    initSpeed: Number,
    index: Number
  },
  data: function () {
    return {
      x_pos: 10,
      y_pos: 10,
      angle: this.initAngle,
      width: 100,
      height: 100,
      speed: this.initSpeed ? this.initSpeed : 1
    }
  },
  computed: {
    transStyle: function () {
      return `transform: translate(${this.x_pos}px,${this.y_pos}px);`
    }
  },
  methods: {
    getNextAngle: function (borderName, angle) {
      if (angle > 360) {
        angle %= 360
      }
      switch (borderName) {
        case 'top':
          return 360 - angle
        case 'right':
          return 540 - angle
        case 'bottom':
          return 360 - angle
        case 'left':
          return 180 - angle
        default:
          break
      }
    },
    getIfArriveBorder: function () {
      if (this.x_pos <= 0) {
        this.x_pos = 0
        return 'left'
      }
      if (this.y_pos <= 0) {
        this.y_pos = 0
        return 'top'
      }
      if (this.x_pos + this.width >= this.borderWidth) {
        this.x_pos = this.borderWidth - this.width
        return 'right'
      }
      if (this.y_pos + this.height >= this.borderHeight) {
        //   alert(`${this.y_pos},${this.height},${this.borderHeight},angle:${this.angle}`)
        this.y_pos = this.borderHeight - this.height
        return 'bottom'
      } else {
        return false
      }
    },
    getNextPos: function () {
      let border = this.getIfArriveBorder()
      if (border) {
        this.angle = this.getNextAngle(border, this.angle)
      }
      this.x_pos += this.speed * Math.cos((this.angle / 180) * Math.PI)
      this.y_pos += this.speed * Math.sin((this.angle / 180) * Math.PI)
    },
    updatePos: function () {
      this.getNextPos()
      console.log(this.angle)
      setTimeout(() => {
        this.updatePos()
      }, 5)
    },
    clickHandler: function() {
      alert('cxk')
    }
  },
  created () {
    this.updatePos()
  }
}
</script>

<style scoped>
* {
  color: rgb(63, 161, 226);
  display: inline-block;
  position: absolute;
  user-select: none;
}
img {
  height: 100px;
}
#tag {
  z-index: 2;
  font-size: 5em;
  color: rgb(102, 155, 184);
}
</style>
