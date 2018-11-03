<template>
  <div class="utc-clock">
    <h1>UTC</h1>
    <div class="time">
      <span class="hour">{{hours}}:</span>
      <span class="minute">{{minutes}}:</span>
      <span class="second">{{seconds}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "UTCClock",
  data() {
    return {
      now: new Date()
    }
  },
  computed: {
    hours() {
      let h = this.now.getUTCHours();
      return h < 10 ? `0${h}` : h;
    },
    minutes() {
      let m = this.now.getUTCMinutes();
      return m < 10 ? `0${m}` : m;
    },
    seconds() {
      let s = this.now.getUTCSeconds();
      return s < 10 ? `0${s}` : s;
    }
  },
  mounted() {
    setInterval(() => {
      this.now = new Date();
    }, 200);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
