<template>
 <h1> hellow from reaction timer</h1>
 <button class="button" @click="start" :disabled="isPalying" :class="{disabled : isPalying}"> play </button>
 <Block v-if="isPalying" :delay="delay" @end="endGame" />
 <!-- <p v-if="showResults"> reaction time is {{score}}   ms </p> -->
 <Results v-if="showResults" :score="score" />
<div class="soundes" v-if="isPalying">
  <audio autoplay>
  <source src="./assets/short-success.mp3" type="audio/ogg">
Your browser does not support the audio element.
</audio>
</div>
</template>

<script>
import Block from './components/block.vue'
import Results from './components/results.vue'
export default {
  name: 'App',
  components: { Block,Results },
  data() {
    return {
      isPalying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start()
    {
      this.isPalying = !this.isPalying
      this.delay = 2000 + Math.random() * 5000
      console.log(this.delay);
      this.showResults = false

    },
    endGame(reactionTime){

      this.score = reactionTime,
      this.isPalying = false,
      this.showResults = true

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
.button {
  background-color: #4CAF50; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}
.button:hover {
  background-color: #3e8e41;
}
.disabled {
  opacity: 0.6;
  cursor: not-allowed;
}
</style>
