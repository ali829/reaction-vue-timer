<template>
  <div v-if="!isPlay && !showResult" class="speed-test" @click="play">
  </div>
  <result v-if="showResult" :reactionScore="result" />
  <block v-if="isPlay" :delay="delay" @yourreaction="endGame" />
</template>

<script>
  import block from "./components/block.vue";
  import result from "./components/result.vue";


  export default {
    name: 'App',
    components: {
      block,
      result
    },
    data: () => ({
      isPlay: false,
      isWait: false,
      showResult: false,
      delay: null,
      result: 0
    }),
    methods: {
      play() {
        this.delay = 2000 + Math.random() * 5000;
        this.isWait = true;
        this.isPlay = true;
        this.showResult = false;
      },
      endGame(reactionTime) {
        this.result = reactionTime;
        this.isPlay = false;
        this.isWait = false;
        this.showResult = true;
      }
    }
  }
</script>

<style>
  body {
    margin: 0;
  }

  .speed-test {
    height: 100vh;
    width: 100vw;
    background-color: #a6d6d6;
  }

  .wait-container {
    height: 100vh;
    width: 100vw;
    background-color: #f55c47;
  }
</style>