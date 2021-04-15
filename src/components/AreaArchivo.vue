<template>
<div v-if="files.length == 0" class="caja" v-cloak @drop.prevent="addFile" @dragover.prevent>
<h4>Drag and Drop here</h4>
<li v-for="(file,id) in files" :key="id" class="list-group-item mb-3 border-top">
{{ file.name }} ({{ file.size }} kb)
<button @click="removeFile(file)">Remove</button>
</li>
<br>
</div>
<div v-if="files.length > 0">
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
<table class="table">
<thead v-if="excelData.header != null">
<tr>
<td scope="col" v-for="(h,i) in excelData.header.length" :key="i">{{excelData.header[i]}}</td>
</tr>
</thead>
<tbody>
<tr scope="row" v-for="item of excelData.results" :key="item" >
<td>{{item.id}}</td>
<td>{{item.nombre}}</td>
<td>{{item.clave}}</td>
<td><button class="btn btn-success">Consultar</button></td>
</tr>
</tbody>
</table>
</div>
</div>
</div>
</div>
</div>
</template>
<script>
import XLSX from 'xlsx'
export default{
name: 'AreaArchivo',
data: function() {
return{
files: [],
loading: false,
excelData: {
header: null,
results: null
}
}
},
methods: {
addFile(e) {
let files = e.dataTransfer.files;
[...files].forEach(file => {
this.files.push(file);
console.log("files -> "+this.files)
this.readerData(files[0])
});
},
removeFile(file) {
this.files = this.files.filter(f => {
return f != file;
});
},
generateData({ header, results }) {
this.excelData.header = header
this.excelData.header.push("acciones")
this.excelData.results = results
},
readerData(rawFile) {
this.loading = true
return new Promise((resolve) => {
const reader = new FileReader()
reader.onload = e => {
const data = e.target.result
const workbook = XLSX.read(data, { type: 'array' })
const firstSheetName = workbook.SheetNames[0]
const worksheet = workbook.Sheets[firstSheetName]
const header = this.getHeaderRow(worksheet)
const results = XLSX.utils.sheet_to_json(worksheet)
console.log("header -> "+header)
console.log("results -> "+results)
this.generateData({ header, results })
this.loading = false
resolve()
}
reader.readAsArrayBuffer(rawFile)
})
},
getHeaderRow(sheet) {
const headers = []
const range = XLSX.utils.decode_range(sheet['!ref'])
let C
const R = range.s.r
/* start in the first row */
for (C = range.s.c; C <= range.e.c; ++C) { /* walk every column in the range */
const cell = sheet[XLSX.utils.encode_cell({ c: C, r: R })]
/* find the cell in the first row */
let hdr = 'UNKNOWN ' + C // <-- replace with your desired default
if (cell && cell.t) hdr = XLSX.utils.format_cell(cell)
headers.push(hdr)
}
return headers
},
isExcel(file) {
return /\.(xlsx|xls|csv)$/.test(file.name)
}
}
}
</script>
<style>
.caja{
position:relative;
margin:20px;
padding: 0px 10px;
/*height:auto;*/
border:2px dashed #999;
text-align:center;
margin-top:10px;
}

.caja ul li span{
position:absolute;
top:0;
right:0;
cursor:pointer;
width:30px;
height:30px;
text-align:center;
line-height:30px;
background:white;
z-index:1;
color:white;
background: red;
}	
</style>