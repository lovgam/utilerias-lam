<template>
<div class="container">
<div class="card">
<div class="car-header">
<h4>Datos del cliente</h4>
</div>
<img class="card-img-top rounded" src="../assets/logo.png" alt="Card image cap">
<div class="card-body">
<ul class="list-group list-group-flush">
<li class="list-group-item lead">{{nombre}}</li>
<li class="list-group-item">Cliente unico: {{clienteUnico}}</li>
<li class="list-group-item">ZG Originación: {{zgOri}}</li>
<li class="list-group-item">ZG Cobranza: {{zgCob}}</li>
<li class="list-group-item">Solicitud pendiente</li>
</ul>
<p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
</div>
</div>
</div>
</template>
<script>
export default{
name: 'DatosCliente',
data: function (){
	return{
		nombre:'Sara Ramos Domínguez',
		clienteUnico: '0101-0987-9929-8',
		zgOri: '1-15-492',
		zgCob: '1-34-654'
	}
}
}
</script>