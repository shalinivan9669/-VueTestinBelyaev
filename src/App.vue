<template>
  <div class="app">
    <add-stopwatch-button @addStopwatch="addStopwatch" />
    <stopwatch-list :stopwatches="stopwatches" />
  </div>
</template>

<script>

import StopwatchList from './components/StopwatchList.vue';

export default {
  name: 'App',
  components: {
    StopwatchList,
  },
  data() {
    return {
      stopwatches: [],
    };
  },
  methods: {
    addStopwatch() {
      this.stopwatches.push({ id: Date.now() });
    },
  },
};
</script>

<style>
body{
  background-color: #353638;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100%;
  height: 100%;
}
* {
    margin: 0;
    padding: 0;
   }
   stopwatch-list{
    display: flex;
  flex-direction: column;
   }
</style>
