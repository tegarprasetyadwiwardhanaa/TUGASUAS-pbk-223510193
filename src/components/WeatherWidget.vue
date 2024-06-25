<template>
    <q-card class="weather-widget">
      <q-card-section class="input-section">
        <div class="text-h6">Cuaca Realtime</div>
        <q-input
          v-model="location"
          placeholder="Masukkan Lokasi"
          @keyup="startLoading"
          @keyup.enter="getWeather"
          dense
        >
          <template v-slot:append>
            <q-btn @click="getWeather" label="Cari" color="primary" />
          </template>
        </q-input>
      </q-card-section>
      <q-card-section v-if="loading" class="loading-section">
        <q-spinner color="primary" />
        <div class="text-body2 q-ml-sm">Loading...</div>
      </q-card-section>
      <q-card-section v-if="weather" class="weather-info">
        <div class="row items-center">
          <div class="col-auto">
            <img :src="weatherIcon" alt="Weather Icon" class="weather-icon" />
          </div>
          <div class="col">
            <div class="text-subtitle1">{{ weather.name }}</div>
            <div class="text-subtitle2">{{ weather.weather[0].description }}</div>
            <div class="text-h4">{{ weather.main.temp }}°C</div>
            <div class="text-body2">Min: {{ weather.main.temp_min }}°C | Max: {{ weather.main.temp_max }}°C</div>
            <div class="text-body2">Kelembaban: {{ weather.main.humidity }}%</div>
            <div class="text-body2">Angin: {{ weather.wind.speed }} m/s</div>
            <div class="text-body2">Tekanan: {{ weather.main.pressure }} hPa</div>
            <div class="text-body2">Matahari Terbit: {{ sunrise }}</div>
            <div class="text-body2">Matahari Terbenam: {{ sunset }}</div>
            <div class="text-body2 q-mt-sm">Update terakhir: {{ updatedAt }}</div>
          </div>
        </div>
      </q-card-section>
      <q-card-section v-if="error">
        <q-banner type="negative" icon="warning">
          {{ error }}
        </q-banner>
      </q-card-section>
    </q-card>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'WeatherWidget',
    data() {
      return {
        location: '',
        weather: null,
        loading: false,
        error: null,
        apiKey: 'a624c752fdba6d03a2470726fb03f651' // Ganti dengan API Key Anda
      };
    },
    computed: {
      weatherIcon() {
        if (this.weather && this.weather.weather[0]) {
          return `http://openweathermap.org/img/wn/${this.weather.weather[0].icon}@2x.png`;
        }
        return '';
      },
      sunrise() {
        if (this.weather && this.weather.sys) {
          return new Date(this.weather.sys.sunrise * 1000).toLocaleTimeString();
        }
        return '';
      },
      sunset() {
        if (this.weather && this.weather.sys) {
          return new Date(this.weather.sys.sunset * 1000).toLocaleTimeString();
        }
        return '';
      },
      updatedAt() {
        return new Date().toLocaleTimeString();
      }
    },
    methods: {
      startLoading() {
        this.loading = true;
        this.weather = null;
        this.error = null;
      },
      async getWeather() {
        if (!this.location) return;
        this.loading = true;
        this.error = null;
        this.weather = null;
        try {
          const response = await axios.get(
            `https://api.openweathermap.org/data/2.5/weather?q=${this.location}&units=metric&appid=${this.apiKey}`
          );
          this.weather = response.data;
        } catch (error) {
          this.error = 'Error fetching weather data. Please try again.';
          console.error('Error fetching weather data', error);
        } finally {
          this.loading = false;
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .weather-widget {
    max-width: 500px;
    margin: 20px auto;
    border-radius: 15px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    transition: transform 0.3s;
  }
  
  .weather-widget:hover {
    transform: translateY(-5px);
  }
  
  .input-section {
    background-color: #f1f1f1;
    padding: 20px;
  }
  
  .loading-section {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px;
  }
  
  .weather-info {
    background-color: #fff;
    padding: 20px;
  }
  
  .weather-icon {
    width: 100px;
    height: 100px;
  }
  
  .text-subtitle1,
  .text-subtitle2 {
    font-weight: bold;
  }
  
  .text-h4 {
    color: #ff5722;
  }
  
  .text-body2 {
    margin-top: 5px;
  }
  </style>
  