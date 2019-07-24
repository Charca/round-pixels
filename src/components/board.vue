<template>
  <div class="board">
    <div v-for="row in circles">
      <circle v-for="circle in row" :color=circle.color :active=circle.active></circle>
    </div>
  </div>
</template>

<script>
import Circle from './circle.vue';

export default {
  data () {
    return {
      rows: 9,
      columns: 9,
      circles: []
    }
  },

  props: {
    colors: {
      required: true
    }
  },

  events: {
    'color-selected': 'paintCircles'
  },

  components: {
    Circle
  },

  ready() {
    for(var i = 0; i < this.rows; i += 1) {
      this.circles.push([]);

      for(var j = 0; j < this.columns; j += 1) {
        this.circles[i].push({color: this.generateRandomColor(), active: false});
      }
    }

    this.circles[0][0].active = true;

    // Activate all touching neighbours that share the same color with the first circle
    this.paintCircles(this.circles[0][0].color);
  },

  methods: {
    generateRandomColor() {
      var randomIndex = Math.floor(Math.random() * (this.colors.length));
      return this.colors[randomIndex];
    },

    paintCircles(color) {
      for(var i = 0; i < this.rows; i += 1) {
        for(var j = 0; j < this.columns; j += 1) {
          if(this.circles[i][j].active) {
            // All actives get the new color
            this.circles[i][j].color = color;
            this.activateNeighboursWithIndex(i, j, color);
          } // End if active
        } // End j loop
      } // End i loop
    },

    activateNeighboursWithIndex(i, j, color) {
      var neighbours = {
        top: this.circles[i-1] && this.circles[i-1][j],
        right: this.circles[i][j+1],
        bottom: this.circles[i+1] && this.circles[i+1][j],
        left: this.circles[i][j-1]
      };

      for(var key in neighbours) {
        if(neighbours[key] && !neighbours[key].active && neighbours[key].color === color) {
          neighbours[key].active = true;
        }
      } // End neighbours loop
    }
  }
}
</script>

<style>
  .board {
    margin-bottom: 60px;
  }
</style>