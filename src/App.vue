<template>
  <div class="black" :style="{width: this.blackWidth + '%'}"></div>
  <div class="beige" :style="{width: this.beigeWidth + '%'}"></div>
  <div class="text__wrapper">
    <transition name="slide-fade">
      <div class ="counter" v-if="this.timer < 100">
        <div class = "text">
          <p>{{ Math.round(this.timer) }}</p>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  data(){
    return{
      timer:0,
    }
  },

  methods:{
    loadingIncrement(){
      const interval = setInterval(() => {
        this.timer+=0.1;

        if(this.timer > 100){
          clearInterval(interval);
        }
      }, 1);
    },

  },

  computed:{
    blackWidth(){
      if(this.timer > 100){
        return 100;
      }
      else{
        return this.timer;
      }
    },

    beigeWidth(){
      return Math.max(0, 100 - this.timer);
    }
  },

  watch:{
    
  },

  mounted() {
    this.loadingIncrement();
  },
}
</script>

<style>
  @font-face {
    font-family: 'Forum';
    src: url('./assets/fonts/Forum-Regular.ttf');
  }

  * {
    margin: 0;
    padding: 0;
    outline: 0;
    box-sizing: border-box;
  }
  
  body {
   -webkit-font-smoothing: antialiased;
   font-family: 'Forum';
  }
  
  button {
   cursor: pointer;
  }

  .beige{
    position: absolute;
    right: 0;
    background:  #AB8867;
    min-height: 100vh;
  }

  .black{
    position: absolute;
    left:0;
    height: 100vh;
    background-color: #1D1D1D;
  }

  .counter{
    width: 100%;
    height: 800px;
  }

  .text{
    background: transparent;
    font-size: 200px;
    line-height: 200px;
    cursor:default;
    text-align:center;
    color:white;
  }

  .text__wrapper{
    position: absolute;
    top:25vh;
    width: 100vw;
    height: 200px;
    overflow: hidden;
  }

  .slide-fade-enter-active {
    transition: all 0.3s ease-out;
  }

  .slide-fade-leave-active {
    transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
  }

  .slide-fade-enter-from,
  .slide-fade-leave-to {
    transform: translateY(200px);
  }

  .text{
    font-size:200px;
    margin: 0;
    padding: 0;
  }

  svg{
    height: 200px;
  }

  p{
    color:white;
    font-size:200px;
    text-align:center;
  }
</style>