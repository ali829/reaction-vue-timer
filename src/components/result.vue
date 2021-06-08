<template>
    <div class="result-container">
        <p>your reaction Time :{{reactionScore}} ms</p>
        <p class="rank">{{ rank }}</p>
    </div>
</template>

<script>
    export default {
        name: "result",
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
        color: #0faf87;
        font-weight: bold;
    }

    .result-container {
        height: 100vh;
        width: 100vw;
        background-color: #a6d6d6;
    }
</style>