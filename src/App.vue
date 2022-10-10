<template>
  <h1> Reaction Ninja</h1>
  <button :disabled="isPlaying" @click="start"> Start Game </button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
  <Results v-if="showResults" :score="score"> </Results>
</template>

<script>

import Block from "@/components/Block";
import Results from "@/components/Results";
export default {
  name: 'App',
  components: {
    Results,
    Block
  },

  data() {
    return {
      isPlaying: false,
      delay : null,
      score: null,
      showResults : false
    }
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random()*5000;
      console.log(this.delay)
      this.showResults = false;
    },
    endGame(reactionTime){
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    }
  },
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
  background: green;
}
button[disabled]{
  cursor: not-allowed;
  opacity: 0.2;
}
</style>
