<template>
<div class="row p-3">
<div class="col-3">
<button class="btn btn-success" data-toggle="modal" data-target="#exampleModal">Cargar archivo</button>
</div>
<div class="col-3">
<button class="btn btn-success">Descargar</button>
</div>
<div class="col-3">
<button class="btn btn-danger">Cancelar</button>
</div>
<div class="col-3">
<button class="btn btn-success">Actualizar</button>
</div>
</div>
<div class="modal fade bd-example-modal-lg" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
<div class="modal-dialog modal-lg" role="document">
<div class="modal-content">
<div class="modal-header">
<h5 class="modal-title" id="exampleModalLabel">Clientes a modificar</h5>
<button type="button" class="close" data-dismiss="modal" aria-label="Close">
<span aria-hidden="true">&times;</span>
</button>
</div>
<div class="modal-body">
<AreaArchivo/>
</div>
<div class="modal-footer">
<button type="button" class="btn btn-secondary" data-dismiss="modal">Cerrar</button>
</div>
</div>
</div>
</div>
</template>
<script>
import AreaArchivo from '@/components/AreaArchivo.vue'
export default{
name: 'Botones',
components:{
	AreaArchivo
}
}
</script>