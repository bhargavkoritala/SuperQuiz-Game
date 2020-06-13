<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-lg-6 col-md-6 col-sm-6">
                <h5 class="border border-info">What is the value of {{firstNumber}} {{operationValue(operation)}} {{secondNumber}} ?</h5>
                <div class="p-2 row">
                    <div class="col-lg-6 col-md-6 col-sm-6" :key="index" v-for="(answer,index) in variables">
                    <p @click="answered(index)" class="alert alert-primary">{{answer}}</p>
                </div>
                </div>
                
            </div>
            
        </div>
    </div>
</template>

<script>
export default {
    name : 'Question',
    data(){
        return{
            firstNumber : 0,
            secondNumber : 0,
            operation : 0,
            variables : [],
            gTruth : [false,false,false,false]
        }
    },
    methods : {
        operationValue(number){
            if(number==0){
                return '+'
            }
            else if(number ==1){
                return '-'
            }
            else{
                return '*'
            }
        },
        answered(value){         
            if(this.gTruth[value]){
                this.$emit('answered',1)
            }
            else {
                this.$emit('answered',0)
            }
        },
        getRandomInt(min, max) {
            min = Math.ceil(min);
            max = Math.floor(max);
            return Math.floor(Math.random() * (max - min)) + min;
        }
    },
    mounted(){
        this.firstNumber = Math.floor(Math.random() * 100)
        this.secondNumber = Math.floor(Math.random() * 100)
        this.operation = Math.floor(Math.random() * 3)
        var answer;
        var pos = Math.floor(Math.random() * 4);
        if(this.operation==0){
            answer = this.firstNumber + this.secondNumber
        }
        else if(this.operation==1){
            answer = this.firstNumber - this.secondNumber
        }
        else{
            answer = this.firstNumber * this.secondNumber
        }
        for(let i =0;i<4;i++){
            this.variables.push(this.getRandomInt(answer-10,answer+10))
        }
        console.log('position: '+pos)
        this.variables[pos] = answer
        this.gTruth[pos]=true
        console.log(this.gTruth)
    }

}
</script>

<style scoped>
    p{
        cursor: pointer;
    }
</style>