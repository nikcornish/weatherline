<template>
  <div id="app">
    <linetest v-if="!isFetching" :chartdata="weatherdata"></linetest>
  </div>
</template>

<script>
import Linetest from '@/components/Linetest.vue';
export default {
  name: 'App',
  components: {
    Linetest
  },

  data: function() {
    return {
      lat: 48.069247,
      long: 11.891291,
      weatherdata: null,
      isFetching: true,
      config: {
        headers: {
          'x-rapidapi-host': process.env.VUE_APP_HOST,
          'x-rapidapi-key': process.env.VUE_APP_KEY
        }
      }
    }
  },

  computed: {
    formattedCoords() {
      return `${this.lat},${this.long}`
    },
    requestUrl() {
      return `https://weatherapi-com.p.rapidapi.com/forecast.json?days=3&q=${this.formattedCoords}`
    },
    maxTemps() {
      return this.weatherdata.forecast.forecastday.map(x => Math.floor(x.day.maxtemp_c));
    },
    maxTempsTotal() {
      return this.maxTemps.reduce((a,c) => Math.floor(a+c));
    }
  },
  
  methods: {
    getData() {
      try {
        this.axios.get(this.requestUrl, this.config)
          .then(response => {
            this.weatherdata = response.data;
            this.isFetching = false;
          });
      } catch(err) {
        console.log(err);
      } 
    }
  },

  created() {
    this.getData();
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
