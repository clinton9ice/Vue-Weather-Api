<template>
  <div class="container-fluid row justify-content-between m-0 p-0">
    <LeftSidebar class="col-xl-8 col-sm-10 left" :forCast="weather.forecast"></LeftSidebar>
    <RightSidebar class="col-xl-4 col-sm-5 right" :weatherLocation="weather" @submit ="searchVal"></RightSidebar>
  </div>
</template>

<script>
import RightSidebar from "@/components/RightSidebar";
import LeftSidebar from "@/components/LeftSidebar";

export default {
  components: {
    RightSidebar,
    LeftSidebar,
  },
  data() {
    return {
      weather: [],
      defaultSearch: "Asaba",
      searchCount: 8,
      hosted: false,
      httpsCall: "https://api.weatherapi.com/v1/current.json?",
      ApiKey: "d8bd9b82587e4b81b67221333222803",
      http: "http://api.weatherapi.com/v1/forecast.json?"
    };
  },
  methods: {
    async  fetchWeather(search = this.defaultSearch, count = this.searchCount) {
      let req = await fetch(
        `${this.hosted? this.httpsCall: this.http}key=${this.ApiKey}&q=${search}&days=${count}&aqi=yes`
      );
      return req.json();
    },

    async searchVal(e){
      let req = await fetch(
        `${this.hosted? this.httpsCall: this.http}key=${this.ApiKey}&q=${e}&days=${this.searchCount}`
      );
      this.weather = await req.json();
    }
  },
  created: async function () {
    this.weather = await this.fetchWeather();
  }
};
</script>

<style>
/*.left_bg {*/
/*  background-color: var(--bs-gray-200);*/
/*}*/

@media screen and (max-width: 900px) {
  .left {
    width: 100% !important;
    flex: none;
  }
  .container-fluid {
    flex-wrap: wrap-reverse !important;
  }
}
</style>
