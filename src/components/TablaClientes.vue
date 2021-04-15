<template>
<div id="accordion" class="pb-3">
<div class="card">
<div class="card-header" id="headingOne">
<h5 class="mb-0">
<button class="btn btn-link" data-toggle="collapse" data-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">
Clientes a modificar
</button>
</h5>
</div>
<div id="collapseOne" class="collapse show" aria-labelledby="headingOne" data-parent="#accordion">
<div class="card-body">
<table class="table" :data="tableData">
<thead>
<tr>
<td scope="col" v-for="item of tableData" :key="item" :prop="item" :label="item">#</td>
<td scope="col">Nombre</td>
<td scope="col">Cliente unico</td>
<td scope="col">Acciones</td>
</tr>
</thead>
<tbody>
<tr scope="row">
<td>1</td>
<td>Sara Ramos Domínguez</td>
<td>0101-0987-9929-8</td>
<td><button class="btn btn-success">Consultar</button></td>
</tr>
</tbody>
</table>
</div>
</div>
</div>
</div>
</template>
<script>
export default{
name: 'TablaClientes',
props: ["data"],
data() {
    return {
      tableData: [],
      tableHeader: []
    }
  },
}
</script>