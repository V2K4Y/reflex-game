<template>
  <div class="container">
  <h1>Reaction - time Game </h1>
  <h2>Click the button to start the game.</h2>
  <p>** After hitting the button a green color box will appear on the page. Click that box as quickly as you can. **</p>

  <button @click="startGame" :disabled="isPlaying">Play the game</button>
  <Block v-if="isPlaying" :delay="delay" @end-game="stopGame"></Block>
 
  <Result v-if="showResult" :reactionTime="recTime"></Result>
  </div>

  <!-- <p v-if="showResult">Your Reaction Time is {{recTime}}ms</p> -->
</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';



export default {
  name: 'App',
  components: {
    Block,
    Result,

  },

  data() {
    return {
      isPlaying: false,
      delay: null,
      recTime: null,
      showResult: false,
    }
  },

  methods: {

    startGame() {

      this.delay = 2000 + Math.random() * 5000;
      // console.log(this.delay) 
      this.isPlaying = !this.isPlaying;
      this.showResult = false;
    },

    stopGame(reactionTime) {

      this.isPlaying = false;

      this.recTime = reactionTime;
      this.showResult = true;
      // console.log(reactionTime) ;
    }


  }
}
</script>

<style>
  body{
    background-color: rgb(77, 77, 77);
    align-items: center;
  }
  .container{
    margin: 10px auto;
    padding: 10px;
    width: 60em;
    height: 600px;
    border-radius: 15px;
    border-top: 6px darkolivegreen solid;
    background-color:  rgb(60, 60, 60);
    box-shadow: 10px 10px 5px rgb(55, 55, 55);
  }
  button{
    /* padding: 5px; */
    border: 0px black solid;
    display: inline-block;
    margin: 20px;
    padding: 10px;
    border-radius: 5px;
    background-color: rgb(140, 140, 140);
  }
  button:hover{
    box-shadow: 5px 5px 2px rgb(40, 40, 40);
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #5c8ebf;
  margin-top: 60px;
}
</style>
