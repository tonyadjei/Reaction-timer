<template>
  <h1>Quikk reaction timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block @endTimer="endGame" v-if="isPlaying" :delay="delay" />  <!-- if you might use life cycle hooks like mounted() or updated() then stick to v-if, and not v-show -->
  <Results v-if="displayResult" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      displayResult: false
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.displayResult = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.displayResult = true
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
  color: #444;
  margin-top: 60px;
}
button{
  background: #0faf87;
  color: white;
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
