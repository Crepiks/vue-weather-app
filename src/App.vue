<template>
  <div class="wrapper">
    <weather-picture class="wrapper__item"></weather-picture>
    <div class="wrapper__item bordered">
      <weather-info :weather-description="weatherDescription" :temp="temp"></weather-info>
      <weather-form @get-data="getCurrentWeather" @change-city="changeCity"></weather-form>
    </div>
  </div>
</template>

<script>
import WeatherForm from './components/Form';
import WeatherInfo from './components/Weather';
import WeatherPicture from './components/Picture';

import settings from './config/api';

export default {
  name: 'app',
  components: {
    'weather-picture': WeatherPicture,
    'weather-form': WeatherForm,
    'weather-info': WeatherInfo
  },
  data () {
    return {
      cityName: settings.deafultCity,
      temp: null,
      weatherDescription: ''
    }
  },
  methods: {
    getCurrentWeather() {
      fetch(`https://api.openweathermap.org/data/2.5/weather?q=${this.cityName}&appid=${settings.apiKey}&units=metric`)
      .then((response) => {
        response.json().then((data) => {
          this.temp = data.main.temp;
          this.weatherDescription = data.weather[0].description;
          console.log(this.cityName);
        })
      })
    },
    changeCity(newCity) {
      this.cityName = newCity;
    }
  }
}
</script>

<style lang="scss">

@import url('https://fonts.googleapis.com/css?family=Open+Sans');

* {
  margin: 0;
  padding: 0;
}

body {
  font-family: "Open Sans", serif;
}

.wrapper {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;

  background: rgba(45,176,224,1);
  background: -moz-linear-gradient(45deg, rgba(45,176,224,1) 0%, rgba(96,40,168,1) 100%);
  background: -webkit-gradient(left bottom, right top, color-stop(0%, rgba(45,176,224,1)), color-stop(100%, rgba(96,40,168,1)));
  background: -webkit-linear-gradient(45deg, rgba(45,176,224,1) 0%, rgba(96,40,168,1) 100%);
  background: -o-linear-gradient(45deg, rgba(45,176,224,1) 0%, rgba(96,40,168,1) 100%);
  background: -ms-linear-gradient(45deg, rgba(45,176,224,1) 0%, rgba(96,40,168,1) 100%);
  background: linear-gradient(45deg, rgba(45,176,224,1) 0%, rgba(96,40,168,1) 100%);
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#2db0e0', endColorstr='#6028a8', GradientType=1 );

  &__item {
    width: 40%;
    height: 55vh;

    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
}

.bordered {
  border-top: 2px solid #113a65;
  border-bottom: 2px solid #113a65;
  border-right: 2px solid #113a65;
}

// .main {
//   height: 55vh;
//   background: #2a6bb1;
//   box-shadow: 0px 2px 80px -20px rgba(0,0,0,0.5);
//   width: 60%;
//   margin: 0 auto;
// }

// .error {
//   color: #041f3c;
//   font-weight: bold;
// }
</style>
