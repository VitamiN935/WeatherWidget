<template>
  <div class="wrapper">
    <div class="wrapper wrapper__wind">
      <SvgDirection />
      <span>{{ windSpeed }}m/s {{ directionWind }}</span>
    </div>
    <div class="wrapper wrapper__wind">
      <SvgInfo />
      {{ pressure }}hPA
    </div>
  </div>
</template>

<script lang="ts" setup>
import { computed } from "@vue/runtime-core";
import SvgDirection from "../Svg/SvgDirection.vue";
import SvgInfo from "../Svg/SvgInfo.vue";

interface Props {
  pressure: number;
  windSpeed: number;
  windDeg: number;
}
const props = defineProps<Props>();

const directionWind = computed(() => {
  const dir = props.windDeg;
  if (dir > 348.75 && dir <= 11.25) return "N";
  else if (dir > 11.25 && dir <= 33.75) return "NNE";
  else if (dir > 33.75 && dir <= 56.25) return "NE";
  else if (dir > 56.25 && dir <= 78.75) return "ENE";
  else if (dir > 78.75 && dir <= 101.25) return "E";
  else if (dir > 101.25 && dir <= 123.75) return "ESE";
  else if (dir > 123.75 && dir <= 146.25) return "SE";
  else if (dir > 146.25 && dir <= 168.75) return "SSE";
  else if (dir > 168.75 && dir <= 191.25) return "S";
  else if (dir > 191.25 && dir <= 213.75) return "SSW";
  else if (dir > 213.75 && dir <= 236.25) return "SW";
  else if (dir > 236.25 && dir <= 258.75) return "WSW";
  else if (dir > 258.75 && dir <= 281.25) return "W";
  else if (dir > 281.25 && dir <= 303.75) return "WNW";
  else if (dir > 303.75 && dir <= 326.25) return "NW";
  else return "NNW";
});
</script>