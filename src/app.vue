<template>
  <div class="app">
    <h1>{{msg}}</h1>
    <board :colors=colors></board>
    <controls :colors=colors></controls>
  </div>
</template>

<script>
import Board from './components/board.vue';
import Controls from './components/controls.vue';

export default {
  data() {
    return {
      msg: 'Round Pixels',
      colors: [ 'red', 'blue', 'green', 'orange', 'purple', 'gray' ]
    }
  },

  events: {
    'color-selected': function(color) {
      this.$broadcast('color-selected', color);
    }
  },

  components: {
    Board,
    Controls
  }
}
</script>

<style>
  body {
    background: #31495A;
    color: #FFF;
    font-family: Helvetica, sans-serif;
    text-align: center;
  }
</style>