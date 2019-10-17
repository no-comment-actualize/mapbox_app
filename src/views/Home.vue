<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div id='map'></div>
  </div>
</template>

<style>
  body { 
    margin:0; 
    padding:0; 
  }
  #map { 
    top:0; 
    bottom:0; 
    height:700px;
  }
</style>

<script>
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!"
    };
  },
  created: function() {},
  mounted: function() {
    mapboxgl.accessToken = 'pk.eyJ1IjoiZHphZ2hpYW4iLCJhIjoiY2pzbnF0NmV0MGY2czQzbXBpMjcwMzRmNiJ9.Jei4-17Vu7hJSerisjPCEg';
    var map = new mapboxgl.Map({
        container: 'map', // container id
        style: 'mapbox://styles/mapbox/streets-v11', // stylesheet location
        center: [-122.431297, 37.773972], // starting position [lng, lat]
        zoom: 12 // starting zoom
    });
  },
  methods: {}
};
</script>