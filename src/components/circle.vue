<template>
  <div class="circle {{color}}"></div>
</template>

<script>
  export default {
    props: {
      color: {
        default: 'red'
      },
      active: {
        default: false
      }
    }
  }
</script>

<style>
  .circle {
    width: 30px;
    height: 30px;
    display: inline-block;
    margin: 0 7px 7px 0;
    border-radius: 15px;
    box-shadow: 0 0 5px rgba(0, 0, 0, .5);
  }

  .red {
    background: linear-gradient(to bottom, #E53935 0%, #E35D5B 100%);
  }

  .blue {
    background: linear-gradient(to bottom, #457FCA 0%, #5691C8 100%);
  }

  .green {
    background: linear-gradient(to bottom, #1EB27E 0%, #48DB7E 100%);
  }

  .orange {
    background: linear-gradient(to bottom, #FFB347 0%, #FFCC33 100%);
  }

  .purple {
    background: linear-gradient(to bottom, #9D50BB 0%, #7E4BCF 100%);
  }

  .gray {
    background: linear-gradient(to bottom, #8E9EAB 0%, #B6CBD0 100%);
  }
</style>