<template>
  <h1> {{score}}ms </h1>
  <p> {{rank}}</p>
</template>

<script>
export default {
  name: "Results",
  props:["score"],
  data() {
    return {
      rank: null
    }
  },
  mounted() {
    if(this.score < 250){
      this.rank = "Master"
    }
    else if (this.score < 500){
      this.rank = "Aprentice"
    }
    else
      this.rank = "Banana"
  }
}
</script>

<style scoped>

</style>