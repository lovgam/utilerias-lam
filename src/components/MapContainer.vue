<template>
  <div ref="map-root"
       style="width: 100%; height: 400px;">
  </div>
</template>

<script>
  import View from 'ol/View'
  import Map from 'ol/Map'
  import TileLayer from 'ol/layer/Tile'
  import OSM from 'ol/source/OSM'
  import VectorLayer from 'ol/layer/Vector'
  import VectorSource from 'ol/source/Vector'

  import 'ol/ol.css'

  export default {
    name: 'MapContainer',
    components: {},
    props: {
    },
    data: () => ({
      olMap: null,
      vectorLayer: null,
      selectedFeature: null
    }),
    mounted() {
      this.vectorLayer = new VectorLayer({
        source: new VectorSource({
          features: [],
        }),
      })

      this.olMap = new Map({
        target: this.$refs['map-root'],
        layers: [
          new TileLayer({
            source: new OSM(),
          }),
          this.vectorLayer
        ],
        view: new View({
          zoom: 0,
          center: [0, 0],
          constrainResolution: true
        }),
      })
    }
  }
</script>
