<template>
  
  <h1 class="title">The Reaction Time Test</h1>
  <div class="square"></div>
  <marquee behavior="" direction="" width="20%"><h4>So you think you can move fast | Wow, come on lets test your reaction.</h4></marquee>
  <br>
  
  <button @click="start" :disabled="isPlaying">Play</button>

  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score="score"/>


</template>

<script>

import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random()*5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>

<style>
body {
  background: #eee;
}
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  button {
    background: #6f0faf;
    color: whitesmoke;
    border: 2px solid whitesmoke;
    padding: 8px 16px;
    border-radius: 4px;
    font-size: 16px;
    letter-spacing: 1px;
    cursor: pointer;
    margin: 18px;
  }
  button[disabled]{
    opacity: 0.2;
    cursor: not-allowed;
  }
  .square {
    width: 300px;
    height: 5px;
    background: #2c3e50;
    border-radius: 5px;
    margin: 0 auto;
  }
  h1.title {
    margin-bottom: 0;
  }

</style>
