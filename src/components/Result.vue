<template>
  <p>Reaction Time - {{reactionTime}} ms</p>
  <h1 class="rank">{{rank}}</h1>
</template>

<script>
export default {
    props:['reactionTime'],
    data(){
      return {
        rank:""
      }
    },
    mounted(){
      if(this.reactionTime<=250){
        this.rank = "Ninja Fingers"
      }else if(this.reactionTime<=400){
        this.rank = "Rapid Reflexes"
      }else if(this.reactionTime>400){
        this.rank = "Snail Pace ..."
      }
    }
}
</script>

<style>
.rank{
  /* font-weight: bold; */
  color: #0faf87

}
</style>