<template>
  <div class="py-4">
    <h5 class="title p-3">Hourly</h5>
    <div class="weather-container" v-for="hours in weatherHour.forecastday" v-bind:key="hours">


      <div class="weather-days my-4" v-for="hour in hours.hour" v-bind:key="hour.time"
           :class="[hour.time.split(' ')[0].split('-')[2] === today? 'active': '' ]">
        <div class="days-icon">
          <img :src="hour.condition.icon" alt="">
        </div>
        <div class="days">
          {{ days[Math.round(hour.time.split(" ")[0].split("-")[2])] + ", " + hour.time.split(" ")[1] }}
        </div>
        <div class="days-dgree">{{ hour.wind_degree }}<sup>o</sup></div>
      </div>

    </div>
  </div>
</template>

<script>
let date = new Date().getDate();
export default {
  props: {
    weatherHour: Array,
  },
  data() {
    return {
      days: ["Thurs", "Friday", "Sat", "Sun", "Mon", "Tues", "Wed"],
      today: date < 10 ? "0" + date : date
    }
  }
};
</script>

<style scoped>
.weather-container .weather-days {
  max-width: 120px;
  padding: 1rem;
  background: #fff;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  box-shadow: 0 9px 6px #00000012;
  margin: 0 0.5rem;
  flex-basis: 100%;
  flex-shrink: 0;
  min-height: 120px;
  transition: all 200ms ease;
  cursor: pointer;
}
</style>
