<template>
  <h2 class="time text-primary">{{ time }} {{ format }}</h2>
  <span class="date text-dark"
    >{{ day }}, {{ date }} {{ month }}, {{ year }}</span
  >
</template>

<script>

export default {
  data() {
    return {
      year: "",
      month: "",
      date: "",
      day: "",
      time: "",
      format: ""
    };
  },
  methods: {
    updateTime() {
      const date = new Date();

      const day = ["Sun", "Mon", "Tues", "Wed", "Thurs", "Friday", "Sat"];

      const months = [
        "Jan",
        "Feb",
        "Mar",
        "April",
        "May",
        "Jun",
        "July",
        "Aug",
        "Sept",
        "Oct",
        "Nov",
        "Dec",
      ];
      const mins = date.getMinutes();
      var hours = date.getHours();
      let renTimer = hours%12

      this.year = date.getFullYear();
      this.month = months[date.getMonth()];
      this.date = date.getDate();
      this.day = day[date.getDay()];
      this.time = `${renTimer ? renTimer : 12}:${mins < 10 ? "0" + mins : mins}`;
      this.format = hours >= 12 ? 'pm' : 'am';
    },
  },

  created() {
    this.updateTime();

    //   Dynamically update the time
    setInterval(this.updateTime, 6000);
  },
};
</script>

<style lang="scss" scoped></style>
