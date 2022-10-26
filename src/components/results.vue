<template>
    <div class="result">
        <p class="score"> reaction time is {{ score }} ms </p>
        <p class="rank"> your rank are {{ rank }} </p>
    </div>
</template>


<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null,
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = "Ninga Ranked"
        }
        else if (this.score < 400) {
            this.rank = "hero Ranked"
        }
        else if (this.score < 600) {
            this.rank = "horse Ranked"
        }
        else if (this.score < 1000) {
            this.rank = "monkey Ranked"
        }
        else {
            this.rank = "donkey Ranked"
        }
    },

}
</script>

<style scoped>
.rank {
    color: crimson;
    padding: 50px 0;
    margin: 0 auto;
    font-weight: bolder;
    font-size: xx-large;
    
}
.score{
    color: rgb(58, 158, 8);
    padding: 50px 0;
    margin: 0 auto;
    font-weight: bolder;
    font-size: xx-large;
}
</style>