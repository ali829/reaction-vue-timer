<template>
      <div class="wait-svg">
          <div style="--delay:1"></div>
          <div style="--delay:2"></div>
          <div style="--delay:3"></div>
      </div>
</template>

<script>
export default {
  name: "wait"
}
</script>

<style scoped>
    .wait-svg{
      height: auto;
      width: 60%;
      max-width: 90%;
      display: flex;
      justify-content: center;
      align-items: center;
      margin: 10px auto;
    }
    .wait-svg div{
      width: 50px;
      height: 50px;
      border-radius: 50%;
      background-color: #ffffff;
      margin: 7px;
      transition: all .4s ease-in-out;
      animation: waitAnimation .4s ease forwards infinite;
    }

    @keyframes waitAnimation {
        0%{
          transform: translateY(0);
          animation-delay: calc(var(--delay));
        }
        50%{
          transform: translateY(20%);
          animation-delay: calc(var(--delay));
        }
        100%{
          transform: translateY(0);
          animation-delay: calc(var(--delay));
        }
    }
</style>