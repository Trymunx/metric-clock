<template>
  <div id="app">
    <UTCClock/>
    <MetricClock/>
  </div>
</template>

<script>
import UTCClock from "./components/UTCClock.vue";
import MetricClock from "./components/MetricClock.vue";

export default {
  name: "app",
  components: {
    UTCClock,
    MetricClock
  }
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.hour {
  font-size: 2em;
  color: #4e4e5a;
}
.minute {
  font-size: 2em;
  color: #4e4e5a;
}
.second {
  font-size: 2em;
  color: #5e5e6a;
}
.time {
  padding: 10px;
  margin: 20px;
}
</style>
