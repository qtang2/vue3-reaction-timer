<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
  <!-- <p v-if="showResult">Reaction Time {{score}} ms</p> -->
  <Result v-if="showResult" :reactionTime="score"></Result>
</template>

<script>
import Block from './components/Block'
import Result from './components/Result'

export default {
  name: 'App',
  data(){
    showBlock:false
  },
  components: {
    Block,
    Result
  },
  data(){
    return {
      isPlaying:false,
      delay:null,
      score: null,
      showResult: false
    }
  },
  methods:{
    start(){
      this.isPlaying = true,
      this.delay = 2000 + Math.random()*5000
      this.showResult = false
      console.log(this.delay)
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button{
   background: #0faf87;
   color: #fff;
   border: none;
   padding: 8px 16px;
   border-radius: 4px;
   font-size: 16px;
   letter-spacing: 1px;
   cursor: pointer;
   margin: 10px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
