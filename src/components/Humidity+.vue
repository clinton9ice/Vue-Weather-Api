<template>
  <div class="card-container my-5" v-if="foreCast">

    <div class="card" v-for="days in foreCast.forecastday" v-bind:key="days.day.condition.code">
      <div class="card-header small text-dark fw-bold"> {{day[Math.abs(days.date.split("-")[2])].toUpperCase()}} - Humidity</div>

      <div class="card-body my-1">
        <span class="percent text-success">{{days.day.avghumidity}}%</span>
      </div>

      <div class="card-footer small text-muted">{{days.day.condition.text}}</div>
    </div>

  </div>
</template>

<script>
export default {
  props: {
    foreCast: Object
  },
  data() {
    return {
      day: ["Thurs", "Friday", "Sat", "Sun", "Mon", "Tues", "Wed"],
    }
  }
}
</script>

<style lang="css" scoped>
.card-container {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
}

.card-container .card {
  max-width: 200px;
  width: 100%;
  box-shadow: 7px 20px 9px #00000012;
  margin: 1rem;
}

.card-container .card .card-body {
  font-size: 2em;
}
</style>
