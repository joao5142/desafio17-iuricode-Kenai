<template>
  <p class="date">
    {{ hours }}:{{ minutes }}:{{ seconds }}
    {{ ampm }}
  </p>
</template>

<script>
export default {
  name: "Date",
  data() {
    return {
      hours: this.getFormatedHours(),
      seconds: this.getFormatedSeconds(),
      minutes: this.getFormatedMinutes(),
      ampm: this.getAmPm(),
    };
  },
  mounted() {
    setInterval(this.setData, 1000);
  },
  methods: {
    setData() {
      this.hours = this.getFormatedHours();
      this.minutes = this.getFormatedMinutes();
      this.seconds = this.getFormatedSeconds();
      this.ampm = this.getAmPm();
    },
    getFormatedHours() {
      let date = new Date();
      let hours = date.getHours();
      return hours < 10 ? `0${hours}` : hours;
    },
    getFormatedMinutes() {
      let date = new Date();
      let minutes = date.getMinutes();
      return minutes < 10 ? `0${minutes}` : minutes;
    },
    getFormatedSeconds() {
      let date = new Date();
      let seconds = date.getSeconds();
      return seconds < 10 ? `0${seconds}` : seconds;
    },
    getAmPm() {
      let date = new Date();
      let hours = date.getHours();
      return hours >= 12 ? "PM" : "AM";
    },
  },
};
</script>

<style lang="scss" scoped>
.date {
  font-family: "Open Sans";
  font-weight: 300;

  font-size: 2.1rem;
  color: $white-color;
  display: inline-block;
}
</style>