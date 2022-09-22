<template>
    <h2>Your Reaction time is: {{reactionTime}} (ms)</h2>
</template>

<script>
import { watch } from '@vue/runtime-core'
export default {
 name : 'Result',
 props:['reactionTime'] ,

 data(){
    return{
        time : this.reactionTime ,
    }
 },

 watch : {
     time(val , newVal ){
         console.log(newVal) ;
     }
 }
}
</script>

<style scoped>
h2{
    display: block;
    margin-top: 6rem;
    /* color: bisque; */
    color: rgb(124, 155, 69);
}

</style>