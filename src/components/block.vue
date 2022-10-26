<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
    </div>
   
</template>

<script>

export default {
    props: ['delay'],

    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay);
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            }, 10);
        },
        stopTimer() {
            clearInterval(this.timer);
            this.$emit('End', this.reactionTime)
            console.log(this.reactionTime)
        }


    },
    updated() {
        console.log("updated")
    },
    unmounted() {
        console.log("unmounted")
    },

}
</script>

<style>
.block {
    width: 400px;
    border-radius: 10px;
    background-color: rgb(44, 108, 87);
    color: white;
    text-align: center;
    padding: 100px 0px;
    margin: 40px auto;
}
</style>