<script >
import { GoogleMap, AdvancedMarker } from 'vue3-google-map'

export default {
  components: { GoogleMap, AdvancedMarker },
  data: (vm) => ({
    showMap: false,
    markers: [
      { mapCenter: { lat: 39.6313364, lng: -119.6760433 } }
    ]
  }),
  methods: {
    toggleMap() {
      this.showMap = !this.showMap
    }
  }
}
</script>

<template>
  <div style="display:flex;width:500px;height:200px">
    <div>
      <button @click="toggleMap">Toggle Map</button>
    </div>

    <GoogleMap
      api-key="your_key"
      style="height:200px;width:200px;margin-left:20px"
      :center="markers[0].mapCenter"
      mapId="your_map_id"
      :zoom="12"
      v-if="showMap">
        <AdvancedMarker 
          :key="index"
          v-for="(m, index) in markers"
          :options="{ position: m.mapCenter }" 
        />
    </GoogleMap>
  </div>
</template>
