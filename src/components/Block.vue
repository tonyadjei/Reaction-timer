<template>
  <div v-if="showBlock" class="block" @click="stopTimer">
      click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data(){
        return {
            showBlock: false,
            reactionTime: 0,
            timer: null
        }
    },
    //mounted is a life cycle hook fired when the component is mounted in the DOM
    mounted(){ // life cycle hooks are placed directly in the component object, and not inside the 'methods' property
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods:{
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer(){
            clearInterval(this.timer)
            //the only way to send data back up from a child component to a parent component is to use custom events(indicating the data to be sent as the 2nd parameter of the $emit function)
            this.$emit('endTimer', this.reactionTime) //we are passing data we can access in the parent component as a second argument to the this.$emit() funciton
            //now, by specifying a data along with the event, the function that handles the event inside the parent component, takes as a parameter the data we passed along.
        }
    }
}
</script>

<style>
    .block{
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>