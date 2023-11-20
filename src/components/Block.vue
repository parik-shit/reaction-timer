<template>
  <div class="block" v-if="showBlock" @click = "stopTimer">click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return { showBlock: false, timer: null, reactionTime: 0 };
  },
  methods: {
    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime)
      
      this.$emit('end' , this.reactionTime) // emmiting the "end" event 
    },
      startTimer(){
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10)
    }
    
    
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay)
  },
  updated() {
    console.log(this.showBlock);
  },
  unmounted(){
    
  }
};
</script>

<style>
.block {
  width: 80%;

  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
