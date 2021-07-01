<template>
  <div class="result-wrapper">
    <div class="result">
      <h3 :class="{'red' : reactionTime > 600, 'green' : reactionTime < 600}">Your Reaction Time is: {{ reactionTime }} ms</h3>
      <button @click="playAgain">Play Again</button>
       <p>{{ reactionTime > 600? "You need to do better than that!" : "Good Job!" }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['reactionTime'],
  
  methods:{
    playAgain(){
      this.$emit('playAgain')
    }
  }
}
</script>


<style scoped>
  .result-wrapper{
    padding: 3em;
    display: flex;
    justify-content: center;  
  }

  .result{
    color: white;
    background-color: rgb(14, 68, 99);
    width: 300px;
    height: 200px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 5px;
  }

  h3.red{
    color: red;
  }

  h3.green{
    color: green;
  }

</style>