<template>
    <h1>reaction timer</h1>
    <button @click="play" :disabled="isPlay">play</button>
    <result v-if="showResult" :reactionScore="result" />
    <block v-if="isPlay" :delay="delay" @yourreaction="endGame" />
</template>

<script>

import block from "./components/block.vue";
import result from "./components/result.vue";


export default {
  name: 'App',
  components: {block , result},
  data: ()=> ({
      isPlay : false,
      showResult : false,
      delay : null,
      result : 0
  }),
  methods : {
    play() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlay = true;
      this.showResult = false;
    },
    endGame(reactionTime){
      this.result = reactionTime;
      this.isPlay = false;
      this.showResult = true;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #4444;
  margin-top: 60px;
}
button{
  padding:5px 20px;
  border-radius: 4px;
  color: azure;
  appearance: none;
  border: none;
  background-color: cadetblue;
  outline: none;
  cursor: pointer;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);;
}
button[disabled]{
    opacity: 0.4;
    cursor: not-allowed;
}
</style>
