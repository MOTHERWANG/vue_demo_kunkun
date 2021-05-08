<template>
  <div id="app">
    <Cxk :initAngle="angle1" :index=5 :initSpeed="2.996" :borderWidth="borderWidth" :borderHeight="borderHeight" />
    <Cxk :initAngle="angle1" :index=4 :initSpeed="2.997" :borderWidth="borderWidth" :borderHeight="borderHeight" />
    <Cxk :initAngle="angle1" :index=3 :initSpeed="2.998" :borderWidth="borderWidth" :borderHeight="borderHeight" />
    <Cxk :initAngle="angle1" :index=2 :initSpeed="2.999" :borderWidth="borderWidth" :borderHeight="borderHeight" />
    <Cxk :initAngle="angle1" :index=1 :initSpeed="3.0"   :borderWidth="borderWidth" :borderHeight="borderHeight" />
    

  </div>
</template>

<script>
// import func from 'vue-editor-bridge';
// import Vue from 'vue'
import Cxk from "./components/cxk";

export default {
  name: "App",
  components: {
    Cxk,
  },
  data: function () {
    return {
      angle1: 45,
      angle2: 20,
      angle3: 30,
      angle4: 40,
      borderWidth: window.innerWidth,
      borderHeight: window.innerHeight,
      // angle: 45,
    };
  },
  methods: {
    
  },
  created() {
    // setInterval(() => {
    //   this.updatePos();
    // }, 1);
    // // console.log(this.getNextAngle("bottom", 405));
    window.addEventListener("resize", () => {
      this.borderWidth = window.innerWidth;
      this.borderHeight = window.innerHeight;
    });
    // setInterval(() => {
      
    // }, 100);
  },
};
</script>

<style>
#app {
}
</style>
