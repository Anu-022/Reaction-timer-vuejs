<template>
    <p>Reaction Time is: {{score }} ms</p>
    <p>{{rank }}</p>
</template>

<script>
  export default {
    props:['score'],
    data() {
        return {
            rank:'',
        }
    },
    mounted() {
        if (this.score <= 500) {
            this.rank ='💪🏻 Super Fast!';
        } else if (this.score <= 1500) {
            this.rank = '👏🏻 Rapid Reflex!';
        } else {
            this.rank ='👎🏻 Snail Pace!'
        }
    }
  }

</script>