<template>
  <div class="controls">
    <button v-for="color in colors" v-on:click="selectColor(color)" class="control circle {{color}}"></button>
  </div>
</template>

<script>
import Circle from './circle.vue';

export default {
  props: {
    colors: {
      required: true
    }
  },

  components: {
    Circle
  },

  methods: {
    selectColor(color) {
      this.$dispatch('color-selected', color);
    }
  }
}
</script>

<style>
  .control {
    outline: none;
    width: 46px;
    height: 46px;
    border-radius: 23px;
    margin-right: 10px;
  }

  .control:last-child {
    margin-right: 0;
  }
</style>