<template>
    <div class="result-container" @click="newGame">
        <div>
          <watch />
          <h1>{{reactionScore}} ms</h1>
          <h3>click to play again</h3>
        </div>
    </div>
</template>

<script>
import watch from "./svgs/watch.vue";
    export default {
        name: "result",
        components:{watch},
        props: {
            reactionScore: {
                type: Number,
                default: 0,
                required: false
            }
        },
        data: () => ({
            rank: null
        }),
        methods:{
          newGame(){
            this.$emit('newgame')
          }
        },
        mounted() {
            if (this.reactionScore < 250) {
                this.rank = 'so fast like minato...';
            } else if (this.reactionScore < 400) {
                this.rank = 'rapid reaction...';
            } else {
                this.rank = "snail..."
            }
        }
    }
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: #58b368;
        font-weight: bold;
    }

    .result-container {
        height: 100vh;
        width: 100vw;
        background-color: #2a6fdb;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .result-container h1 {
      margin: 10px auto;
      color: #ffffff;
      font-size: 4em;
      margin-bottom: 10px;
      text-transform: capitalize;
      font-family: "Agency FB";
    }
    .result-container h3 {
      color: #ffffff;
      font-size: 1.2em;
      text-transform: capitalize;
      font-family: "Agency FB";
      text-align: center;
    }
</style>