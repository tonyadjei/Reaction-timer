<template>
    <p>Reaction time is {{ score }}ms</p>
    <p class="mark">{{ mark }}</p>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return{
            mark: null
        }
    },
    mounted(){
        if(this.score < 250){
            this.mark = "Super quickk!!"
        }
        else if(this.score < 400){
            this.mark = "Rapid reflexes"
        }
        else{
            this.mark = "Snail pace..."
        }
    }

}
</script>

<style>
.mark{
    font-size: 1.4rem;
    color: #0faf87;
    font-weight: bold;
}
</style>