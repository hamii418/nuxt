<template>
 <div >
  <div class="fixed">垂直方向のスクロール量：<span>{{ scrollY }}</span></div>
  <p class="height1">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor ......
  </p>
  <div :class="{ 'fade': scrollY > 900 }"></div>
  <p class="height1">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor ......
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor ......
  </p>
 </div>
</template>

<style>
.fixed {
  position: fixed;
  top: 0;
}

p {
  height: 1000px;
  background-color: pink;  
}
</style>

<script>
 export default {
  data() {
   return {
    scrollY: 0
   }
  },
  mounted() {
   window.addEventListener('scroll', this.calculateScrollY);
  },
  beforeDestroy() {
   window.removeEventListener('scroll', this.calculateScrollY);
  },
  methods: {
   calculateScrollY() {
    this.scrollY = window.scrollY;
   }
  }
 }
</script>

