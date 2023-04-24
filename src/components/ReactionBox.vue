<template>
    <div v-if="showBlock" class="reaction-box" @click="stopTimer">
    Click me
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return{
            showBlock: false,
            timer: null,
            reactionTime: 0,
        }
    },
    mounted(){
       setTimeout(() => {
        this.showBlock = true;
        console.log(this.delay);
        this.startTimer();
       }, this.delay); 

    }, 
    methods: {
        startTimer() {
           this.timer = setInterval(() => {
           this.reactionTime = this.reactionTime + 10;   
           }, 10);
        },
        stopTimer() {
            clearInterval(this.timer);
            this.$emit('end', this.reactionTime);
            console.log(this.reactionTime);
        }

    }    
}


</script>

<style>
.reaction-box {
    width: 500px;
    height:300px;
    background-color: rgb(51, 51, 232);
    border-radius:15px;
    margin: 50px auto;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
}


</style>