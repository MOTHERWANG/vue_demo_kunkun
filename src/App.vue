<template>
  <div id="app">
    <!-- <Cxk :initAngle="angle1" :index=5 :initSpeed="2.996" :borderWidth="borderWidth" :borderHeight="borderHeight" /> -->
    <!-- <Cxk :initAngle="angle1" :index=4 :initSpeed="2.997" :borderWidth="borderWidth" :borderHeight="borderHeight" /> -->
    <!-- <Cxk :initAngle="angle1" :index=3 :initSpeed="2.998" :borderWidth="borderWidth" :borderHeight="borderHeight" /> -->
    <!-- <Cxk :initAngle="angle1" :index=2 :initSpeed="2.999" :borderWidth="borderWidth" :borderHeight="borderHeight" /> -->
    <Cxk :initAngle="angle1" :index=1 :initSpeed="1.0"   :borderWidth="borderWidth" :borderHeight="borderHeight" />
    <Racket/>
  </div>
</template>

<script>
// import func from 'vue-editor-bridge';
// import Vue from 'vue'
import Cxk from './components/cxk'
import Racket from './components/racket'
// import Racket from './components/racket.vue'

export default {
  name: 'App',
  components: {
    Cxk,
    Racket
  },
  data: function () {
    return {
      angle1: 45,

      borderWidth: window.innerWidth,
      borderHeight: window.innerHeight

    }
  },
  methods: {

  },
  created () {
    window.addEventListener('resize', () => {
      this.borderWidth = window.innerWidth
      this.borderHeight = window.innerHeight
    })
  }
}
</script>

<style>
#app {
}
</style>
