<template>
  <div class="wind-box">
    <ul class="list m-0">
      <li class="list-item d-flex align-items-center justify-content-between">
        <div>
          <span>Wind</span>
          <span class="separator mx-3">|</span>
          <span> {{Math.ceil(currentWeather.current? currentWeather.current.wind_mph: 0)}}m/hr</span>
        </div>
        <div class="city small">{{currentWeather.current? currentWeather.current.wind_dir: ''}}</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    currentWeather: Object,
  }
};
</script>

<style scoped>
.wind-box {
  max-width: 300px;
  margin: 2rem auto;
  padding: 1rem;
  border-radius: 8px;
  color: var(--white);
  text-align: center;
}

.wind-box.even {
  background-image: linear-gradient(328deg, var(--pink), #ff9ec2fa);
  box-shadow: -1px 10px 14px #ff75a873;
}
.wind-box.odd {
  background-image: linear-gradient(17deg, #f0c68f, #f7af52);
  box-shadow: -1px 10px 14px #f5bc726b;
}
</style>
