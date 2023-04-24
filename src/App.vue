<template>
  <h1>Reaction Timer</h1>
  <button class="play-btn" @click="playGame"  :disabled="isPlaying">Play</button>
  <div v-if="isPlaying" >
    <ReactionBox :delay="delay" @end="endGame" />
  </div>
  <GameResult v-if="showResults" :score="score"/>
</template>

<script>
import ReactionBox from './components/ReactionBox.vue';
import GameResult from './components/GameResult.vue'
    
export default {
    name: 'App',
    components: {
    ReactionBox,
    GameResult
    },
    data() {
      return {
        isPlaying: false,
        delay: null,
        score: null,
        showResults: false,
      }
     
    },
    methods: {
      playGame() {
        this.isPlaying = true;
        this.delay=  2000 + Math.random() * 5000;
        this.showResults= false;
      },
      endGame(reactionTime) {
        this.score = reactionTime;
        this.isPlaying = false;
        this.showResults = true;
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
.play-btn {
  background-color: rgb(51, 51, 232);
  color: white;
  padding :8px 16px;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
  border: none;
}
.play-btn[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
