<template>
  <div class="container-fluid">
      <div class="row">
        <div class="col-3">
          <!--One of two columns-->
          <DatosCliente/>
        </div>
        <div class="col-9">
          <!--One of two columns-->
          <h4>Mantenimiento de Zonas Geográficas Asignadas</h4>
          <div class="cell cell-map">
            <MapContainer v-on:select="selected = $event"></MapContainer>
          </div>
          <Botones/>
        </div>
      </div>
  </div>
  
</template>

<script>
import 'bootstrap'
import 'jquery'
import '../node_modules/bootstrap/dist/css/bootstrap.min.css'
import MapContainer from './components/MapContainer.vue'
import DatosCliente from './components/DatosCliente.vue'
import Botones from './components/Botones.vue'


export default {
  name: 'App',
  components: {
    MapContainer,
    DatosCliente,
    Botones
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
