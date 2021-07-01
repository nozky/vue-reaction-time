<template>
  <h1>Reaction Timer</h1>
  <button @click="playHandle" :disabled="isPlaying" >Play</button>
  <Block v-if="isPlaying" :delay="delay" @close="stopPlay" />
  <Results v-if="showResult" :reactionTime="reactionTime" @playAgain="playAgain"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  
  data(){
    return{
      delay: null,
      isPlaying: false,
      showResult: false,
      reactionTime: 0
    }
  },

  methods:{
    playHandle(){
      this.delay = 2000 + Math.random() * 1000
      this.isPlaying = true
    },
    stopPlay(reactionTime){
      this.isPlaying = false
      this.reactionTime = reactionTime
      this.showResult = true
    },
    playAgain(){
      this.showResult = false
      this.isPlaying = false
      this.reactionTime = 0
    }
  }
}
</script>

<style>
*{
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

body{
  height: 100vh;
  background-color: whitesmoke;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height:100%;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

}

button{
  margin: 2em;
  padding: 1em 1.5em;
  cursor: pointer;
}
</style>
