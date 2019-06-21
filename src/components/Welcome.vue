<template>
  <v-container fluid justify-center>
    <h1 v-if="timeOfDay" class="text-xs-center display-3">Good {{ timeOfDay }}, {{ name }}</h1>
    <h2 v-if="currentTime" class="text-xs-center display-2">{{ currentTime }}</h2>
  </v-container>
</template>

<script>
export default {
  name: "Welcome",
  data() {
    return {
      timeOfDay: null,
      currentTime: null,
      name: "Ronnie"
    };
  },
  mounted() {
    setInterval(this.setTime, 1000);
  },
  methods: {
    setTime() {
      const now = new Date();
      const h = now.getHours();
      const m = now.getMinutes();
      const s = now.getSeconds();

      this.currentTime = `${this.addZero(h)}:${this.addZero(m)}:${this.addZero(
        s
      )}`;
      this.timeOfDay = this.setTimeOfDay(h);
    },
    setTimeOfDay(hours) {
      // evening if after 5pm, afternoon between 12pm - 5-pm, morning otherwise
      return hours >= 17 ? "evening" : hours >= 12 ? "afternoon" : "morning";
    },
    addZero(num) {
      if (num < 10) return `0${num}`;
      return num;
    }
  }
};
</script>
