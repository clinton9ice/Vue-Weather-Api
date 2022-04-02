<template>
  <div class="py-4 mt-4" v-if="weatherDaily">
    <h5 class="title p-3">Daily</h5>

    <div class="weather-container" v-for="days in weatherDaily.forecastday" v-bind:key="days">

      <div class="weather-days">
        <div class="d-flex">
          <div class="days-icon" :class="[days.day.condition.text.toLowerCase() === 'sunny'? 'sunny': '']">
            <img :src="days.day.condition.icon" :alt="days.day.condition.text">
          </div>

          <div class="detail">
            <h3 class="day">{{ day[Math.abs(days.date.split("-")[2])] }}</h3>
            <p class="date text-muted text-small mb-0">{{ days.date.replaceAll("-", ", ") }}</p>
            <p class="status text-muted">{{ days.day.condition.text }}</p>
          </div>
        </div>

        <div class="days-dgree">
          <span class="avg_tmp" title="average temperature">{{ Math.ceil(days.day.avgtemp_c) }}<sup>o</sup></span>
          <span class="mx_tmp" title="max temperature">{{ Math.ceil(days.day.maxtemp_c) }}<sup>o</sup></span>
        </div>

      </div>

    </div>

  </div>
</template>

<script>
export default {
  props: {
    weatherDaily: Object,
  },
  data() {
    return {
      day: ["Thurs", "Friday", "Sat", "Sun", "Mon", "Tues", "Wed"],
    }
  }
};
</script>

<style scoped>
.weather-container {
  overflow: unset;
  flex-direction: column;
}

.weather-container .weather-days {
  max-width: 100%;
  margin-bottom: 2rem;
  flex-direction: row;
  justify-content: space-between;
  min-height: auto;
}

.days-dgree {
  font-size: 1.2em;
}

.days-icon {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background: hsla(197, 85%, 64%, 35%);
  display: flex;
  justify-content: center;
  align-items: center;
  margin-right: 2rem;
}

.days-icon.sunny {
  background: hsla(34, 78%, 80%, 35%);
}

.days-icon .fa {
  color: var(--white) !important;
}

img {
  width: 50px;
}
</style>
