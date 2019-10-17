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
      message: "Welcome to Vue.js!",
      places: [
        {
          long: -122.421100,
          lat: 37.791930,
          description: "Bob's donuts!"
        },
        {
          long: -122.424970,
          lat: 37.778580,
          description: "Johnny's Donuts!"
        },
        {
          long: -122.025750,
          lat: 36.973800,
          description: "Marini's Downtown Santa Cruz"
        },
        {
          long: -122.037120,
          lat: 37.974730,
          description: "Alpine bakery, Concord!"
        }
      ]
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

    this.places.forEach(function(place) {
      // create the popup
      var popup = new mapboxgl.Popup({ offset: 25 })
      .setText(place.description);

      // create the marker
      new mapboxgl.Marker()
      .setLngLat([place.long, place.lat])
      .setPopup(popup) // sets a popup on this marker
      .addTo(map);
    });

    // var mapboxClient = mapboxSdk({ accessToken: mapboxgl.accessToken });

    // mapboxClient.geocoding.forwardGeocode({
    //     query: 'San Francisco, Ca',
    //     autocomplete: false,
    //     limit: 1
    // })
    //     .send()
    //     .then(function (response) {
    //         if (response && response.body && response.body.features && response.body.features.length) {
    //             var feature = response.body.features[0];

    //             var map = new mapboxgl.Map({
    //                 container: 'map',
    //                 style: 'mapbox://styles/mapbox/streets-v11',
    //                 center: feature.center,
    //                 zoom: 10
    //             });
    //             new mapboxgl.Marker()
    //                 .setLngLat(feature.center)
    //                 .addTo(map);
    //         }
    //     });

  },
  methods: {}
};
</script>