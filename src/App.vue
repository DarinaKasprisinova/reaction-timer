<template>
  <h1>Reaction Time Meter</h1>
  <p>Come and play! Click as fast as you can on green box and find out how fast you are! From God Tier to Snail pace... Good luck my friend</p>
  <button @click="start" :disabled="isPlaying">Play!</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score"></Results>

</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
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

button {
  background-color: #333333;
  color: white;
  border-radius: 15px;
  border: none;
  padding: 15px 30px;
  box-shadow: inset -5px -5px 10px rgba(0, 0, 0, 0.3),
  inset 5px 5px 10px rgba(255, 255, 255, 0.3);
}

button:hover {
  background-color: #555555;
  transform: scale(1.04);
}

button:disabled {
  opacity: 0.2;
  cursor: not-allowed;
  background-color: #999999;
  color: #666666;
  box-shadow: none;
}

</style>
