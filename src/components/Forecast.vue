<template>
  <div class="forecast-box">

    <div class="city-name text-white fw-bold">
      <i class="fa fa-globe me-2"></i>
      {{ weatherLocation.location ? weatherLocation.location.name : ""}}
    </div>

    <div class="ball-effect"></div>

    <div class="forecast-body">
      <div class="thumbnail">

        <div class="img-container">

          <div class="display-4">
            <i class="fa fa-cloud" v-if="weatherLocation.current? !weatherLocation.current.condition.icon: '' "></i>
            <img :src="weatherLocation.current? weatherLocation.current.condition.icon:''" v-else alt="" />
          </div>

          <p class="mt-3 small mb-1">
            {{ weatherLocation.location? weatherLocation.location.localtime.split(" ")[0].replaceAll("-", ", ") :'' }}
          </p>

          <h3 class="display-4">
            {{ Math.ceil(weatherLocation.current? weatherLocation.current.temp_c: 0) }} <sup class="text-sm">o</sup>
          </h3>
        </div>

      </div>

      <p class="mb-1">{{ weatherLocation.current? weatherLocation.current.condition.text : '' }}</p>
      <p class="text-small text-warning">{{ weatherLocation.current? weatherLocation.location.country: '' }}</p>

      <ul class="wind-list list-group rows align-items-center">
        <li class="list-item d-flex align-items-center">
          <span>Wind</span>
          <span class="line-seprate mx-3">|</span>
          <span class="limig">{{weatherLocation.current? weatherLocation.current.wind_degree: ''}} km/ph</span>
        </li>

        <li class="list-item d-flex align-items-center">
          <span>Humidity</span>
          <span class="line-seprate mx-3">|</span>
          <span class="limig"> {{weatherLocation.current? weatherLocation.current.humidity: ''}}% </span>
        </li>
      </ul>

    </div>

  </div>
</template>

<script>
export default {
  props: {
    weatherLocation: Object,
  }
};
</script>

<style scoped>
.forecast-box {
  position: relative;
  padding: 1rem;
  border-radius: 10px;
  max-width: 300px;
  margin: auto;
  box-shadow: 0 12px 7px #1ca4e029;
  background-image: var(--gradient);
  overflow: hidden;
}

.forecast-body {
  max-width: 300px;
  min-height: 300px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: var(--white);
}

.ball-effect {
  height: 60px;
  width: 60px;
  border-radius: 50%;
  position: absolute;
  right: -6px;
  top: -9px;
  box-shadow: -8px 7px 2px 2px #fff2802e, -10px 9px 2px 13px #ffeb3b1f;
  background: #fff280;
}
</style>
