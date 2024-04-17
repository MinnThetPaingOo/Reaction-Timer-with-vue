<template>
<h1>How fast can you catch me?</h1>
<button @click="clickHandlar" :disabled="isPalying==true">Start</button>
<div v-if="isPalying">
  <Block :delay="delay" @stopGame="stopGame"></Block>
</div>

  <div v-if="end==true">
  <Result :score="score"/>

</div>
</template>


<script>
import Block from "./components/Block.vue"
import Result from "./components/Result.vue"
export default {
  name: 'App',
  components: {
    Block,Result
  },
  data(){
    return{
          isPalying : false,
          delay:null,
          score:0,
          end:false
    }
  },
  methods:{
    clickHandlar(){
          this.isPalying=true;
          this.delay=2000+Math.random()*5000;
          this.end=false;
    },
    stopGame(score){
          this.score=score;
          this.isPalying=false;
          this.end=true;
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
