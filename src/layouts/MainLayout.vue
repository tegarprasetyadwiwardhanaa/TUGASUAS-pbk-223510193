<template>
    <q-layout view="hHh lpR fFf">
      <q-header elevated>
        <q-toolbar color="primary">
          <q-btn flat round dense to="/" class="q-toolbar-title">
            WEATHER
          </q-btn>
          <q-space></q-space>
          <q-btn flat round dense>
            TUGAS Tegar
            <q-icon name="arrow_drop_down" />
            <q-menu>
              <q-list style="min-width: 100px">
                <q-item clickable v-ripple tag="a" href="https://tegar-project-cv.netlify.app" target="_blank">
                  <q-item-section>TUGAS 1</q-item-section>
                </q-item>
                <q-item clickable v-ripple tag="a" href="https://tegar-project2.netlify.app" target="_blank">
                  <q-item-section>TUGAS 2</q-item-section>
                </q-item>
                <q-item clickable v-ripple tag="a" href="https://tegar-project3.netlify.app" target="_blank">
                  <q-item-section>TUGAS 3</q-item-section>
                </q-item>
                <q-item clickable v-ripple tag="a" href="https://tegar-project4.netlify.app" target="_blank">
                  <q-item-section>TUGAS 4</q-item-section>
                </q-item>
                <q-item clickable v-ripple tag="a" href="https://tegar-project5.netlify.app" target="_blank">
                  <q-item-section>TUGAS 5</q-item-section>
                </q-item>
                <q-item clickable v-ripple tag="a" href="https://tegar-223510193-tugas6.netlify.app" target="_blank">
                  <q-item-section>TUGAS 6</q-item-section>
                </q-item>
                <q-item clickable v-ripple tag="a" href="https://tegar-223510193-tugas7.netlify.app" target="_blank">
                  <q-item-section>TUGAS 7</q-item-section>
                </q-item>
              </q-list>
            </q-menu>
          </q-btn>
        </q-toolbar>
      </q-header>
  
      <q-page-container>
        <router-view></router-view>
      </q-page-container>
    </q-layout>
  </template>
  
  <script>
  export default {
    name: 'MainLayout'
  };
  </script>
  
  <style scoped>
  .q-toolbar-title {
    text-decoration: none;
    color: #fff;
  }
  
  /* Stylize the toolbar and buttons */
  .q-toolbar {
    padding: 0 20px;
  }
  
  .q-btn {
    min-width: 100px;
    color: #fff;
  }
  
  .q-menu {
    min-width: 150px;
  }
  
  /* Ensure consistent padding */
  .q-page-container {
    padding: 20px;
  }
  
  /* Set a background color for the page */
  .q-layout {
    background-color: #f0f0f0;
  }
  </style>
  