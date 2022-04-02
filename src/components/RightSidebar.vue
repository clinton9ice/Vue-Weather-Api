<template>
  <div class="right-menu">
    <Search class="mb-3 p-3" @search="$emit('submit', $event)"></Search>
    <Forecast :weatherLocation="weatherLocation"></Forecast>
    <RightWindBox class="even" :currentWeather="weatherLocation"></RightWindBox>
  </div>
</template>

<script setup>
import Search from "@/components/Search";
import Forecast from "@/components/Forecast";
import RightWindBox from "@/components/RightWindBox";
import { defineEmits, defineProps } from "vue";

 defineProps({
  weatherLocation: Object,
   search: String
});

defineEmits(["submit"]);
</script>

<style lang="css" scoped>
.right-menu {
  position: fixed;
  right: 0;
  overflow-y: auto;
  background-color: var(--white);
  padding: 1rem 1.4rem;
}

@media screen and (max-width: 900px) {
  .right-menu {
    position: relative;
    width: 100%;
  }
}
</style>
