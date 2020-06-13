<template>
    <div :class="{'border-danger':status=='red','alert-danger':status=='red',
    'border-warning':status=='yellow','alert-warning':status=='yellow',
    'border-info':status=='blue','alert-info':status=='blue'}"
     class="border alert">
        <p>You've scored a total of {{score}}</p>
    </div>
</template>

<script>
export default {
    name:'Score',
    data(){
        return{
            status : ''
        }
    },
    props:{
        score : Number
    },
    created(){
        if(this.score<=15){
            this.status = 'red'
        }
        else if (this.score>15 && this.score<=25){
            this.status = 'yellow'
        }
        else{
            this.status = 'blue'
        }
    }
}
</script>