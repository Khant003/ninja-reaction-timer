<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click me</div>
</template>

<script>
export default {
    props:["delay"],
    data(){
        return{
            showBlock:false,
            timer:null,
            reactionTime:0
        }
    },
    mounted(){
        setTimeout(()=>{
            this.showBlock=true
            this.startTimer();
        },this.delay)
    },
    methods:{
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTime += 10
            },10)
        },
        stopTimer(){
            clearInterval(this.timer)
            console.log(this.reactionTime)
            this.$emit('end',this.reactionTime)
        }
    }
}
</script>

<style>
.block{
    background-color:#de0500;
    max-width:250px;
    margin: 40px auto;
    padding:70px;
    border-radius:10px;
    color:#191919
}
</style>