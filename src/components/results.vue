<template>
    <p>Reaction time: {{ score }}</p>
    <p class="rank">{{ rank }}</p>
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
        if (this.score < 250) {
            this.rank = 'Damn! Are you a Ninja?'
        } else if (this.score < 400) {
            this.rank = 'Quick fingers'
        } else {
            this.rank = 'Are you blind?'
        }
    }
}

</script>

<style>
.rank {
    font-size: 1.4rem;
    color: #0faf87;
    font-weight: bold;
}
</style>