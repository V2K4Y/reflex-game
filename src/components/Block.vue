<template>
    <div class="block" v-if="showBlock" @click="calcReactionTime">
        click Me!
    </div>
</template>

<script>
export default {
    name : 'Block',
    props: ['delay'],
   
    setup(props){
         console.log(props.delay) ;
    } ,
    
    data() {
        return {
            showBlock: false,
            reactionTime: null,
        }
    },

    methods : {
       calcReactionTime(){
          this.reactionTime   =  Date.now() - this.reactionTime ;
        //  console.log(this.reactionTime) ;

          this.$emit('endGame' , this.reactionTime ) ;
       }
    }, 

    beforeCreate() {
       // console.log("before component create state ")
    },

    mounted() {
       // console.log("block component is mounted but dosn't render because v-if state is false ");

        setTimeout(() => {
            this.showBlock = true;
            this.reactionTime = Date.now();
        }, this.delay)
    },


    beforeUpdate() {
        //console.log("this will log before updated life hooks !");
    },

    updated() {
        //console.log("show Block is now set to true ")
    }
}
</script>

<style scoped >
div.block {

    width: 400px;
    border-radius: 20px;
    background: rgb(2, 88, 2);
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
    color: black;
}
</style>