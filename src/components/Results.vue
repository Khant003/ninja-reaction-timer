<template>
  <p class="result">Reaction time : {{score}} ms</p>
  <p class="rank">{{rank}}</p>
</template>

<script>
export default {
    props:['score'],
    data(){
        return{
            rank:null
        }
    },
    mounted(){
        if(this.score < 200){
            this.rank = "Ninja touch"
        } else if(this.score < 250){
            this.rank = "junior ninja touch"
        } else if(this.score < 300){
            this.rank = "rapid touch"
        } else if(this.score < 550){
            this.rank = "normal touch"
        }else if(this.score < 650){
            this.rank = "kid touch"
        } else{
            this.rank = "noob touch"
        }
    }
}
</script>

<style>
.result{
     color: white;
     margin: 30px auto;
     letter-spacing: 1px;
     font-weight: 100;
     font-size: 13px;
 }
 .rank{
     color:#de0500;
     font-weight: bold;
     font-size: 20px;
     margin: 70px 0px auto auto;
 }
</style>