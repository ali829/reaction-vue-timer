<template>
    <div class="block-container" v-if="showBlock" @click="endTimer">
        <p>Click me</p>
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

<style>
    .block {
        width: 400px;
        padding: 100px 0;
        margin: 40px auto;
        background-color: cadetblue;
        border-radius: 10px;
    }

    .block-container {
        height: 100vh;
        width: 100vw;
        background-color: #4aa96c;
    }
</style>