<template>
  <button class="addButton" @click="addStopwatchTimer">
    <span class="plus"></span>
  </button>
</template>

<script>
export default {
  methods: {
    addStopwatchTimer() {
      this.$emit('addStopwatchTimer')
    }
  }
}
</script>

<style>
.addButton {
  margin-bottom: 1rem;
  background-color: #696969;
  border-radius: 5px;
  width: 225px;
  height: 120px;
  position: relative;
  border: none;
}

.addButton::before,
.addButton::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  height: 20px;
  width: 3px;
  background-color: #9E9E9E;
}

.addButton::before {
  transform: translate(-50%, -50%) rotate(90deg);
}

.addButton::after {
  transform: translate(-50%, -50%) rotate(0deg);
}

.addButton:hover::before,
.addButton:hover::after {
  background-color: #d9d9d9;
}

.addButton:focus {
  outline: none;
}

.addButton:focus::before,
.addButton:focus::after {
  background-color: #d9d9d9;
}
</style>