<template>
  <div id="app" class="container-fluid">
    <div class="row justify-content-center">
            <div class="col-lg-8 col-md-8 col-sm-8">
                <h1>Super Quiz</h1>
            </div>
    </div>
    <div class="row justify-content-center">
            <div class="col-lg-8 col-md-8 col-sm-8">
                <component :score="score" :isCorrect="correct" @answered="checkTF" @nextQuestion="toQuestion" :is="which"></component>
            </div>
    </div>
    <div v-if="which!='appScore'" class="row justify-content-center">
            <div class="col-lg-8 col-md-8 col-sm-8">
                <h5>Score :  {{score}}</h5>
            </div>
    </div>
    
  </div>
</template>

<script>

import Answer from './components/Answer';
import Question from './components/Question';
import Score from './components/Score'
export default {
  name: 'App',
  data(){
    return{
      which : 'app-question',
      score : 0,
      correct : false,
      maxQuestions : 1
    }
  },
  components: {
    appQuestion : Question,
    appAnswer : Answer,
    appScore : Score
  },
  methods :{
    checkTF(trueOrFalse){
      console.log(trueOrFalse)
      if(trueOrFalse==1){
        this.score +=4
        this.correct = true
        if(this.maxQuestions==10){
          this.which = 'appScore'
        }
        else{
          this.which = 'app-answer'
        }
      }
      else{
        this.score -=1
        this.correct = false
        if(this.maxQuestions==10){
          this.which = 'appScore'
        }
        else{
          this.which = 'app-answer'
        }
      }
    },
    toQuestion(){
      this.maxQuestions +=1
      this.which = 'appQuestion'
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
</style>
