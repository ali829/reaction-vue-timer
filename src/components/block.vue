<template>
    <div class="block-container" v-if="showBlock" @click="endTimer">
        <div>
          <h1>click!</h1>
        </div>
    </div>
</template>

<script>
    export default {
        name: "block",
        props: {
            delay: {
                type: Number,
                default: null,
                required: true
            },
        },
        data() {
            return {
                showBlock: false,
                timer: null,
                timeReaction: 0
            }
        },
        mounted() {
            setTimeout(() => {
                this.showBlock = true;
                this.startTimer();
            }, this.delay);
        },
        methods: {
            startTimer() {
                this.timer = setInterval(() => {
                    this.timeReaction += 10;
                }, 10)
            },
            endTimer() {
                clearInterval(this.timer);
                this.$emit('yourreaction', this.timeReaction);
            }
        }


    }
</script>

<style scoped>

    .block-container {
        height: 100vh;
        width: 100vw;
        background-color: #309975;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .block-container  h1{
      color: #ffffff;
      font-size: 4em;
      margin-bottom: 10px;
      text-transform: capitalize;
      font-family: "Agency FB";
    }
    .block-container{

    }
</style>