<template>
    <div class="p-2 row justify-content-center">
        <div :class="{'alert-success':isCorrect,'alert-danger':!isCorrect}" class="alert col-lg-6 col-md-6 col-sm-6" role="alert">
            <h4 v-if="isCorrect" class="alert-heading">You've answered it correct !</h4>
            <h4 v-else class="alert-heading">You've answered it Wrong :(</h4>
            <button :class="{'btn-success':isCorrect,'btn-danger':!isCorrect}" class="btn" @click="nextQuestion">Next  question</button>
        </div>
    </div>
</template>

<script>
export default {
    name : 'Answer',
    props :{
        isCorrect : Boolean
    },
    data(){
        return{
            correct : 0
        }
    },
    methods : {
        nextQuestion(){
            this.$emit('nextQuestion')
        }
    }
}
</script>

<style scoped>

</style>