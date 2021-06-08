<template>
    <p>your reaction Time :{{reactionScore}} ms</p>
</template>

<script>
export default {
    name:"result",
    props:{
        reactionScore :{
            type:Number,
            default: 0,
            required: false
        }
    }
}
</script>

<style>

</style>