<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <h2>Click me!</h2>
    <p>Measuring your reaction time...</p>
  </div>
</template>

<script>
export default {
  name: 'Black',
  props:['delay'],

  mounted(){
    this.reactionTime = 0
    setTimeout(()=> { this.showBlock = true }, this.delay)
    this.startTimer()
  },

  data(){
    return{
      showBlock: false,
      timer: null,
      reactionTime: 0   
    }
  },

  methods:{
    close(){
      this.$emit('close', this.reactionTime)
    },

    startTimer(){
      this.timer = setInterval(()=>{ this.reactionTime++ }, 1)
    },

    stopTimer(){
      clearInterval(this.timer)
      this.close()
    }

  },
}
</script>

<style>
  .block{
    background-color: rgb(4, 124, 104);
    
    min-width: 300px;
    max-width: 600px;

    min-height: 200px;
    height: 400px;

    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin: 1em auto;
    color: white;
    padding: 2em 1em;

    border-radius: 5px;

  }
</style>