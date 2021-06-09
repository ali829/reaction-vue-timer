<template>
  <div v-if="!isPlay && !showResult" class="speed-test" @click="play">
      <div>
        <flash />
        <h1>test your reaction time</h1>
        <h3>when the red box turns green , click as quickly as you can.</h3>
        <h3>click any where to start.</h3>
      </div>
  </div>

  <div class="wait-container">
    <div>
      <wait />
      <h1>wait for green</h1>
    </div>
  </div>

  <result v-if="showResult" :reactionScore="result" @newgame="showResult = false"/>
  <block v-if="isPlay" :delay="delay" @yourreaction="endGame" />
</template>

<script>
  import block from "./components/block.vue";
  import result from "./components/result.vue";
  import flash from "./components/svgs/flash.vue";
  import wait from "./components/svgs/wait.vue";


  export default {
    name: 'App',
    components: {
      block,
      result,
      flash, wait
    },
    data: () => ({
      isWait: false,
      isPlay: false,
      showResult: false,
      delay: null,
      result: 0
    }),
    methods: {
      play() {
        this.delay = 2000 + Math.random() * 5000;
        this.isPlay = true;
        this.showResult = false;
      },
      endGame(reactionTime) {
        this.result = reactionTime;
        this.isPlay = false;
        this.showResult = true;
      }
    }
  }
</script>

<style>
  * {
    margin: 0;
  }

  .speed-test {
    height: 100vh;
    width: 100vw;
    background-color: #2a6fdb;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .speed-test div h1{
    color: #81e9e6;
    font-size: 4em;
    margin-bottom: 10px;
    text-transform: capitalize;
    font-family: "Agency FB";
  }
  .speed-test div h3{
    color: #81e9e6;
    font-size: 1.2em;
    text-transform: capitalize;
    font-family: "Agency FB";
    text-align: center;
  }
  .wait-container {
    position: absolute;
    top: 0;
    right: 0;
    z-index: -1;
    height: 100vh;
    width: 100vw;
    background-color: #f55c47;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .wait-container h1 {
    color: #ffffff;
    font-size: 4em;
    margin-bottom: 10px;
    text-transform: capitalize;
    font-family: "Agency FB";
  }
</style>