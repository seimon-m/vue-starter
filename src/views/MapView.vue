<template>
    <link
        href="https://api.mapbox.com/mapbox-gl-js/v1.12.0/mapbox-gl.css"
        rel="stylesheet"
    />
    <h2>My Mapbox</h2>
    <div id="map"></div>
</template>

<script>
// @ is an alias to /src
import mapboxgl from "mapbox-gl";

export default {
    name: "Map",
    data: function() {},
    components: {},
    mounted: function() {
        mapboxgl.accessToken = process.env.VUE_APP_MAPBOX_ACCESS_TOKEN;
        new mapboxgl.Map({
            container: "map",
            style: "mapbox://styles/seimon/ckh3f75gc09mu19nvgrieu4dj", // stylesheet location
            center: [8.30635, 47.05048], // starting position [lng, lat]
            zoom: 13, // starting zoom
        });
    },
};
</script>

<style scoped>
body {
    margin: 0;
    padding: 0;
}
#map {
    position: absolute;
    top: 20;
    bottom: 0;
    width: 100%;
    height: 80%;
}
</style>
