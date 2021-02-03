<template>
  <div v-if="showBlock" class="block">
      click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data(){
        return {
            showBlock: false
        }
    },
    //mounted is a life cycle hook fired when the component is mounted in the DOM
    mounted(){ // life cycle hooks are placed directly in the component object, and not inside the 'methods' property
        setTimeout(() => {
            this.showBlock = true
        }, this.delay)
    },
    updated(){ //life cycle hook fired when data in a component changes
        console.log('data in component has been updated')
    },
    unmounted(){ //life cycle hook fired when a component already mounted in the DOM is removed
        console.log('component has been umounted')
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