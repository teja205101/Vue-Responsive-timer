<template>
  <h1>Hello Timer Project</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <br />
  <ResultsOfTime v-if="showTime" :time="time" />
  <BlockOne v-if="isPlaying" :delay="delay" @click="clickOnBlock" />
</template>

<script>
import BlockOne from "./components/Block.vue";
import ResultsOfTime from "./components/Results.vue";

export default {
  name: "App",
  components: { BlockOne, ResultsOfTime },
  data() {
    return {
      isPlaying: false,
      delay: null,
      intervalId: null,
      time: 0,
      showTime: false,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = Math.random();
      this.intervalId = setInterval(() => {
        this.time++;
      }, 1000);
      this.showTime = false;
      this.time = 0;
    },
    clickOnBlock() {
      clearInterval(this.intervalId);
      this.showTime = true;
      this.isPlaying = false;
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
