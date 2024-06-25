<template>
    <div class="q-pa-md">
      <WeatherWidget />
    </div>
  </template>
  
  <script>
  import WeatherWidget from '../components/WeatherWidget.vue';
  
  export default {
    name: 'Home',
    components: {
      WeatherWidget
    }
  };
  </script>
  
  <style scoped>
  .home-card {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s;
  }
  
  .home-card:hover {
    transform: translateY(-5px);
  }
  
  .text-h6 {
    margin-bottom: 10px;
    color: #333;
  }
  
  .text-subtitle1 {
    color: #666;
  }
  </style>
  