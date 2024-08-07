<template>
  <div class="black"></div>
  <div class="beige"></div>
  <div class="text__wrapper">
    <transition name="slide-fade">
      <div class ="counter" v-if="this.timer < 101">
        <div class = "text">
          <p>{{ this.timer }}</p>
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
        this.timer++;

        if(this.timer == 101){
          clearInterval(interval);
        }
      }, 30);
    },

  },

  computed:{
    
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

  @keyframes increase{
    from{
      width: 0%;
    }
    to{
      width: 100%;
    }
  }

  @keyframes decrease{
    from{
      width: 100%;
    }
    to{
      width: 0%;
    }
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
    width: 100%;
    min-height: 100vh;
    animation: decrease 3s forwards;
  }

  .black{
    position: absolute;
    left:0;
    width: 0%;
    height: 100vh;
    background-color: #1D1D1D;
    animation: increase 3s forwards;
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