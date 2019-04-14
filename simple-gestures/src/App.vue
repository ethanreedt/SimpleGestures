<template>
  <div id="app">
    <div id="gesture-list">
      <Gesture 
        v-for="gest in savedGestures"
        v-bind:key=gest.id
        v-bind:gesture=gest
      />
    </div>
    <!-- <div class="createGesture"></div> -->
  </div>
</template>

<script>
import Gesture from './components/Gesture.vue'

export default {
  name: 'app',
  data: function () {
    return {
      savedGestures: [
        {from: "Ethan", to: "Danny", type: "hugged", comment: "", id: 0}
      ]
    }
  },
  components: {
    Gesture
  },
  methods: {

  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
