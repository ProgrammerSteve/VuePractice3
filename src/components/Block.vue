<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>




<script>
export default {
    data(){
      return {
        showBlock:false,
        timer:null,
        reactionTime:0,
      }
    },
    props:["delay"],
    methods:{
        startTimer(){
            this.timer=setInterval(() => {
            this.reactionTime+=10
            }, 10);
        },

        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end',this.reactionTime)
        }
    },

    mounted(){
        console.log("component mounted")
        setTimeout(() => {
          this.showBlock=true
          this.startTimer()
        }, this.delay);
    },

    updated(){
        console.log("Component Updated:",this.showBlock)
    },

    unmounted(){
        console.log("unmounted")
    }
}

</script>






<style>
  .block{
    width:400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding:100px 0;
    margin:40px auto;

  }
</style>