<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click here</div>
</template>

<script>
export default {

    props:[
        'delay'
    ],
    data(){
        return {
            showBlock:false,
            score:0,
            timer:null

        }
    },
    mounted(){
        setTimeout(() => {
          
          this.showBlock=true;
          this.startTimer();
        },   this.delay);
    },
    methods:{
        startTimer(){
           this.timer=setInterval(() => {
                this.score+=50;
            }, 50);
        },
        stopTimer(){
            clearInterval(this.timer);
           this.$emit("endGame",this.score);
        }
    }


}
</script>

<style>
.block{
    background-color: aqua;
    width: 8em;
    height: 5em;
    margin: 20px auto;
    padding-top: 4em;

}
</style>