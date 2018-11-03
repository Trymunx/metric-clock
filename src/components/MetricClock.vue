<template>
  <div class="metric-clock">
    <h1>Metric</h1>
    <div class="time">
      <span class="hour">{{hours}}:</span>
      <span class="minute">{{minutes}}:</span>
      <span class="second">{{seconds}}</span>
    </div>
    <div class="progress-bar">
      <div class="bar-length"> </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MetricClock",
  data() {
    return {
      now: new Date()
    }
  },
  computed: {
    time() {
      let millisInDay = 24 * 60 * 60 * 1000;
      let time =
        Math.round(100000 *
        (this.now.getHours() * 3600000 +
        this.now.getMinutes() * 60000 +
        this.now.getSeconds() * 1000 +
        this.now.getMilliseconds()) / millisInDay);
      // let s = time.slice(-2);
      // let m = time.slice(-4, -2);
      // let h = time.slice(0, -4);
      //return {h, m, s};
      return time;
    },
    hours() {
      return this.time.toString().slice(0, -4);
    },
    minutes() {
      return this.time.toString().slice(-4, -2);
    },
    seconds() {
      return this.time.toString().slice(-2);
    }
  },
  mounted() {
    setInterval(() => {
      this.now = new Date();
    }, 100);
  },
  watch: {
    time(val) {
      const progressBar = document.querySelector(".bar-length");
      progressBar.style.width = (val / 1000) + "%";
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.metric-clock {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.progress-bar {
  border: solid 1px grey;
  border-radius: 4px;
  width: 80%;
  height: 5px;
}

.bar-length {
  background-color: green;
  height: 5px;
}
</style>
