<template>
    <div class="block" v-if="showBlock" @click="stopTimer"
        :style="{ position: 'absolute', top: top + 'px', left: left + 'px' }">
        Click me
    </div>
</template>
  

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
      top: 0,
      left: 0
    };
  },
  mounted() {
    const screenWidth = window.innerWidth;
    const screenHeight = window.innerHeight;
    const blockWidth = 400;
    const blockHeight = 240;

    this.top = Math.floor(Math.random() * (screenHeight - blockHeight));
    this.left = Math.floor(Math.random() * (screenWidth - blockWidth));

    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
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
      this.$emit('end', this.reactionTime);
    }
  }
};
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>