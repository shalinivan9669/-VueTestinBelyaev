<template>
  <div class="StopWatch">
    <div class="time">
      <h2>{{ name }}</h2>
      <p>{{ formatTime(time) }}</p>
    </div>
    <hr class="separator">
    <div class="buttons">
      <button :class="{'start': !isRunning, 'pause': isRunning}" @click="toggle">
        <span class="triangle" v-if="!isRunning"></span>
        <span class="lines" v-else>
          <span class="line"></span>
          <span class="line"></span>
        </span>
      </button>
      <button class="reset" :style="resetStyle" @click="reset"></button>
    </div>
  </div>
</template>
<script>
export default {
  name: 'StopWatch',
  data() {
    return {
      time: 0,
      timer: null,
      isRunning: false,
      resetStyle: {
        backgroundColor: '#9E9E9E'
      }
    };
  },
  methods: {
    toggle() {
      if (!this.isRunning) {
        this.isRunning = true;
        this.resetStyle.backgroundColor = '#FFFFFF';
        this.timer = setInterval(() => {
          this.time += 1;
        }, 1000);
      } else {
        this.isRunning = false;
        this.resetStyle.backgroundColor = '#9E9E9E';
        clearInterval(this.timer);
        this.timer = null;
      }
    },
    reset() {
      this.isRunning = false;
      this.time = 0;
      this.resetStyle.backgroundColor = '#9E9E9E';
      clearInterval(this.timer);
      this.timer = null;
    },
    formatTime(time) {
      const hours = parseInt(time / 3600);
      const minutes = parseInt((time % 3600) / 60);
      const seconds = time % 60;

      // использование тернарного оператора для обработки числа
      const formattedTime = `${hours ? hours + ':' : ''}${parseInt(minutes) ? parseInt(minutes) + ':' : ''}${seconds}`;
      return formattedTime;
    }
  }
};
</script>

<style>
h2{
  margin-top: 22px;
}
.separator {
  width: 100%;
  border: none;
  border-bottom: 2px solid #9E9E9E;
  margin: 0.5rem 0;
}

.time{
  padding-top: 13px;
}
.StopWatch {
  margin-bottom: 1rem;
  background-color: #696969;
  border-radius: 5px;
  width: 225px;
  height: 120px;
}
.StopWatch h2 {
  margin-top: 0;
}
.StopWatch p {
  font-size: 2rem;
}
.StopWatch .buttons {
  
}

 
.StopWatch button {
  width: 40px;
  height: 40px;
  margin-right: 0.5rem;
  border: none;
  cursor: pointer;
  background-color: transparent;
}
.StopWatch button .triangle {
  display: inline-block;
  width: 0px;
  height: 0px;
  transform: scaleX(-1);
  border-top: 11px solid transparent;
  border-bottom: 11px solid transparent;
  border-right: 15px solid #9E9E9E;
  margin: 0 auto;
}
.StopWatch button.start .triangle {
  border-right-color: #FFFFFF;
}
.StopWatch button .lines {
  display: none;
}
.StopWatch button.pause .lines {
  display: inline-block;
}
.StopWatch button .line {
  display: inline-block;
  width: 3px;
  height: 20px;
  margin: 0 2px;
  background-color: #FFFFFF;
}
.StopWatch button.reset {
  width: 20px;
  height: 20px;
  background-color: #FFFFFF;
  border: none;
  cursor: pointer;

}
</style>
