<template>
  <div v-if="showBlock" class="block" @click="stopTimer" >
    Click Me
  </div>
</template>

<script>
export default {
  name: "Block",
  props: ["delay"],

  mounted() {
    console.log("mounted")
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay)
  },
  updated() {
    console.log("updated")
  },
  unmounted() {
    console.log("unmounted")
  },

  data() {
    return {
      showBlock: false,
      timer : null,
      reactionTime: 0
    }
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer(){
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)
    }
  },
}
</script>

<style scoped>
.block{
  width: 20%;
  height: 50px;
  background: green;
  color: white;
  margin: 40px auto;
}
</style>