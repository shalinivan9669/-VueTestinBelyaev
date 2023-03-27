<template>
  <div class="sss">
  <div  class="stopwatch-list"> 
    <div  v-for="(stopwatchTimer, index) in stopwatchTimers" :key="index">
      <stopwatch-timer :stopwatchTimer="stopwatchTimer" />
    </div>
    <add-StopwatchTimer-button @addStopwatchTimer="addStopwatchTimer" />
  </div>
</div>
</template>

<script>
import StopwatchTimer from './Stopwatch.vue'
import AddStopwatchTimerButton from './AddStopwatchButton.vue'

export default {
  components: {
    StopwatchTimer,
    AddStopwatchTimerButton
  },
  data() {
    return {
      stopwatchTimers: []
    }
  },
  methods: {
    addStopwatchTimer() {
      this.stopwatchTimers.push({ time: 0, isRunning: false })
    }
  }
}
</script>
<style>
 
.stopwatch-list {
  display: flex;
  flex-direction: row;
  gap: 50px;
  flex-wrap: wrap;
  padding: 30px;
  align-items: center;
}

.add-StopwatchTimer-button {
  margin-bottom: 50px;
}
</style>