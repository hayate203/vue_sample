<template>
    <div>
        <h1>マップ</h1>
        <div class="map" id="map" style="height: 500px;width: 100%;"></div>
    </div>
</template>
<script>
import { Loader } from '@googlemaps/js-api-loader';
export default {
    name: "AboutMap",
    components: {
    },
    mounted: function () {
        new Loader({
            apiKey: 'AIzaSyBHN___lO5WF7RFFcMyNE4i1QXDlPuMrn8',
            version: 'frozen',
            libraries: ["places", "drawing", "geometry", "visualization"],
            language: 'ja',
        })
            .load()
            .then((google) => {
                this.google = google;
                // 地図の初期化
                this.map = new google.maps.Map(document.getElementById('map'), {
                    zoom: 7,
                    center: { lat: 35.232, lng: 138.241 },
                });
            })
            .catch(e => {
                console.error(e);
            });
    },
};
</script>