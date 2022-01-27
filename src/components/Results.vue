<template>
  <p>Reaction Time: {{score}} ms</p>
  <p class="rank">{{rank}}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.score < 350){
            this.rank = "You Super Fast!"
        }else if(this.score < 500){
            this.rank = "Rapid Reflexes"
        }else {
            this.rank = "Snail pace..."
        }
    }
}
</script>

<style>
    .rank{
        font-size: 1.4em;
        color: #7c0faf;
        font-weight: bold;
    }
</style>