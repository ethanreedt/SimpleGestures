<template>
  <div id="app">
    <div id="feed">
      <div id="gesture-list-container">
        <div id="gesture-list">
          <Gesture v-for="gest in savedGestures" v-bind:key=gest.id v-bind:gesture="gest"/>
        </div>
      </div>
      <div id="create-gesture">
        <div id="from-container">
          <label for="from">From: </label>
          <input v-model=newGesture.from type="text" id="from">
        </div>
        <div id="to-container">
          <label for="to">To: </label>
          <input v-model=newGesture.to type="text" id="to">
        </div>
        <div id="comment-container">
          <label for="comment">Comment: </label>
          <input v-model=newGesture.comment type="textarea" id="comment">
        </div>
        <button v-on:click="createGesture"></button>
      </div>
    </div>
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
      ],
      newGesture: {
        
      },
      gestureTypes: {
        hug: 'hugged',
        kiss: 'kissed',
        fives: 'high-fived',
        celebrate: 'celebrated with'
      }
    }
  },
  components: {
    Gesture
  },
  methods: {
    createGesture: function () {
      this.newGesture.id = this.savedGestures[this.savedGestures.length - 1].id + 1;
      this.savedGestures.push(this.newGesture);
      this.newGesture = {};
      let inputs = document.getElementsByTagName('input');
      for (let i = 0; i < inputs.length; i++) {
        inputs[i].value = "";
      }
    }
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

#feed {
  position: fixed;
  bottom: 0;
  top: 0;
  right: 0;
  left: 0;
  margin: 0 auto; 
  border: 1px solid lightgrey;
  width: 500px;
}

#gesture-list {
  padding: 15px 5px;
}

#create-gesture {
  position: absolute;
  bottom: 0;
  right: 0;
  left: 0;
  height: 150px;
  border: 1px solid lightseagreen;
}

#create-gesture > #from-container, #create-gesture > #to-container {
  width: 50%;
  display: inline-block;
  
}
</style>
