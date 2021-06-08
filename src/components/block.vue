<template>
    <div class="block" v-if="showBlock" @click="endTimer">
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
        methods:{
            startTimer(){
                this.timer = setInterval(()=>{
                    this.timeReaction += 10;
                } , 10)
            },
            endTimer(){
                clearInterval(this.timer);
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
</style>