<template>
  <div class="header mb-5 p-4">
    <Date></Date>

    <Humidity class="mt-5" :foreCast="forCast"></Humidity>

    <WeatherHourly class="mt-3" :weatherHour = "forCast"></WeatherHourly>

    <WeatherDaily class="mt-3" :weatherDaily="forCast"></WeatherDaily>
  </div>
</template>

<script setup>
import Date from "@/components/Date";
import WeatherHourly from "@/components/WeatherHourly";
import WeatherDaily from "@/components/WeatherDaily";
import Humidity from "@/components/Humidity+";
import {defineProps} from "vue";

 defineProps({
  forCast: Object
});

// console.log(i)

</script>
