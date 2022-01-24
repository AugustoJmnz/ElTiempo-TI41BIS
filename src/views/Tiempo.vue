<template>
  <div v-if="result" class="tiempo">
  <h1><p><b>{{result.name}}</b></p></h1>
 
    <img :src="'http://openweathermap.org/img/w/'+result.weather[0].icon+'.png' " alt=" ">
    <p>{{ result.weather[0].description }}</p>
    <p>Weather: {{ result.main.weather }}</p>
    <p>Degrees: {{ result.wind.deg }}</p>
    <p>Pressure: {{ result.temp.pressure }}</p>
    <p>Humidity: {{ result.temp.humidity }}</p>
    
  </div>
</template>

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
