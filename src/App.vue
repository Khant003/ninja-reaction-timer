<template>
  <h1>Ninja reaction touch</h1>
  <button class="btn" @click="start" :disabled="isplaying">
    <img class="play" src="../src/assets/play-fill.svg">
    <p>Play</p>
  </button>
  <Block v-if="isplaying" :delay="delay" @end="endGame"/>
  <Results :score="score" v-if="showResult"/>
  <img src="../src/assets/ninjabox.png" alt="" class="img" v-if="!isplaying">
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  components:{Block, Results},
  data(){
    return{
      isplaying:false,
      delay:null,
      score:null,
      showResult:false
    }
  },
  methods:{
    start(){
      this.isplaying= true
      this.showResult = false
      this.delay = 2000 + Math.random() * 5000
      console.log(this.delay);
    },
    endGame(reactionTime){
      this.isplaying = false
      this.score = reactionTime
      this.showResult = true
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
  color: #de0500;
  margin-top: 60px;
}
.img{
  margin: 10px auto;
  width:300px
}
.btn{
  margin: 30px auto;
  padding:3px;
  border: none;
  text-align: center;
  background-color: #de0500;
  border-radius: 5px;
  color:white;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  width:100px;
  align-items: center;
  cursor: pointer;
}
.btn[disabled]{
  opacity: 5%;
}
.play{
  color:white;
  padding: auto;
}
App p{
  font-weight: 700;
  letter-spacing: 2px;
}
</style>
