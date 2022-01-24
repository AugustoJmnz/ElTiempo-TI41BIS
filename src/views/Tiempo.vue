<template>
  <div v-if="result" class="tiempo">
  <h1><p><b>{{result.name}}</b></p></h1>
 
    <img :src="'http://openweathermap.org/img/w/'+result.weather[0].icon+'.png' " alt=" ">
    <p>Weather: {{ result.weather[0].description }}</p>
    <p>Temperature: {{ result.main.temp }}</p>
    <p>Pressure: {{ result.main.pressure }}</p>
    <p>Humidity: {{ result.main.humidity }}</p>    
    <p>Degrees: {{ result.wind.deg }}</p>
    <p>Coord (Lon): {{ result.coord.lon }}</p>
    <p>Coord (Lat): {{ result.coord.lat }}</p>
    
  </div>
</template>
<style>

</style>

<script>
import axios from "axios";
export default {
  data: () => ({
    result: null,
  }),
  created() {
      axios
        .get(
            "https://api.openweathermap.org/data/2.5/weather?q=playa%20del%20carmen&APPID=939aae2cc565a6f67803922eca539920")
        .then((result) => {
          this.result = result.data;
          console.log(result.data);
        });
  }
};
</script>
