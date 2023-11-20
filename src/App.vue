<template>
  <h1>Easy Reaction Timer</h1>
  
  <div class="card">
    <div class="tools">
      <div class="circle">
        <span class="red box"></span>
      </div>
      <div class="circle">
        <span class="yellow box"></span>
      </div>
      <div class="circle">
        <span class="green box"></span>
      </div>
    </div>
    <div class="card__content">
      <button class = "button-14" @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" @end = "endGame"/>
  
    <Results v-if = "isEnd" :score = "score"/>
    </div>
  </div>
  
</template>

<script>
import Block from './components/Block'
import Results from './components/Results'

export default {
  name: 'App',
  components: { Block , Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      isEnd: false

    }
  },
  methods: {
    start() {
      // set time amount (ms)
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
    },
    endGame(reactionTime){ //we get this reactionTime as argument from the custom event that is listened @end = "endGame" because we sent the reactionTime from Block.vue while emmiting 
      this.score = reactionTime
      this.isPlaying = false;
      this.isEnd = true

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

.card {
  width: 380px;
  height: 508px;
  margin: 0 auto;
  background-color: #555;
  border-radius: 8px;
  z-index: 1;
}

.tools {
  display: flex;
  align-items: center;
  padding: 9px;
}

.circle {
  padding: 0 4px;
}

.box {
  display: inline-block;
  align-items: center;
  width: 10px;
  height: 10px;
  padding: 1px;
  border-radius: 50%;
}

.red {
  background-color: #ff605c;
}

.yellow {
  background-color: #ffbd44;
}

.green {
  background-color: #00ca4e;
}

/* CSS */
.button-14 {
  background-image: linear-gradient(#f7f8fa, #e7e9ec);
  border-color: #adb1b8 #a2a6ac #8d9096;
  border-style: solid;
  border-width: 1px;
  border-radius: 3px;
  box-shadow: rgba(255, 255, 255, 0.6) 0 1px 0 inset;
  box-sizing: border-box;
  color: #0f1111;
  cursor: pointer;
  display: inline-block;
  font-family: "Amazon Ember", Arial, sans-serif;
  font-size: 14px;
  height: 29px;
  font-size: 13px;
  outline: 0;
  overflow: hidden;
  padding: 0 11px;
  text-align: center;
  text-decoration: none;
  text-overflow: ellipsis;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  white-space: nowrap;
}

.button-14:active {
  border-bottom-color: #a2a6ac;
}

.button-14:active:hover {
  border-bottom-color: #a2a6ac;
}

.button-14:hover {
  border-color: #a2a6ac #979aa1 #82858a;
}

.button-14:focus {
  border-color: #e77600;
  box-shadow: rgba(228, 121, 17, 0.5) 0 0 3px 2px;
  outline: 0;
}
</style>
