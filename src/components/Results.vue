<template>

<p  style="color:orange">Reaction Time: {{ score }} ms</p>
<p class = "Rank" style="color:cyan">{{ rank }}</p>

</template>

<script>
export default {
    props: ['score'],
    data(){
        return {
            rank: null

        }
    },
    mounted(){
        if(this.score < 250 ){
            this.rank = "Wabbit!"

        }
        else if(this.score < 400){
            this.rank = "bombastic!"
        }
        else {
            this.rank = "sloth!"
        }
    }
}

</script>

<style scoped>
.Rank {
    font-size: 2.8em;
    font-weight: bold;
}
</style>