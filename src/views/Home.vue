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
  .mapboxgl-popup {
    max-width: 200px;
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
        style: 'mapbox://styles/dzaghian/cjxaqxm273umk1cqz0saddk4t', // stylesheet location
        center: [-122.431297, 37.773972], // starting position [lng, lat]
        zoom: 12 // starting zoom
    });

    // create the popup
    var popup = new mapboxgl.Popup({ offset: 25 })
    .setText("Bob's Donuts, makes big donuts");

    // create another popup
    var popup2 = new mapboxgl.Popup({ offset: 25 })
    .setText("Johnny's Donuts, makes great cronuts");
     
    // create the marker
    new mapboxgl.Marker()
    .setLngLat([-122.421100, 37.791930])
    .setPopup(popup) // sets a popup on this marker
    .addTo(map);

    // create another marker
    new mapboxgl.Marker()
    .setLngLat([-122.424970, 37.778580])
    .setPopup(popup2) // sets a popup on this marker
    .addTo(map);


  },
  methods: {}
};
</script>