<template>
  <div id="app">
    <l-map :center="[46.2276, 2.2137]" :zoom="5" style="height: 500px;" :options="mapOptions">
      <l-choropleth-layer :data="frDepartmentsData" titleKey="nom" idKey="code" :value="value" :extraValues="extraValues" geojsonIdKey="code" :geojson="franceGeojson" :colorScale="colorScale">
        <template slot-scope="props">
          <l-info-control :item="props.currentItem" :unit="props.unit" title="Department" placeholder="Hover over a department"/>
        </template>
      </l-choropleth-layer>
    </l-map>
  </div>
</template>

<script>
import { InfoControl, ChoroplethLayer } from 'vue-choropleth'
import franceGeojson from '../data/departments.json'
import { frDepartmentsData } from '../data/fr-departments-data'
import {LMap} from 'vue2-leaflet';


export default {
  name: "app",
  components: { 
    LMap,
    'l-info-control': InfoControl, 
    'l-choropleth-layer': ChoroplethLayer 
  },
  data() {
    return {
      frDepartmentsData,
      franceGeojson,
      colorScale: ["e7d090", "e9ae7b", "de7062"],
      value: {
        key: "amount_w",
        metric: "% stat 1"
      },
      extraValues: [{
        key: "amount_m",
        metric: "% stat 2"
      }],
      mapOptions: {
        attributionControl: false
      },
      currentStrokeColor: '3d3e7d090213'
    }
  },
}
</script>
<style>

body {
  background-color: #ffffff;
  margin-left: 100px;
  margin-right: 100px;
}
#map {
  background-color: rgb(238, 238, 238);
}
</style>