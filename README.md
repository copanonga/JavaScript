
# Snippets para JavaScript

## Índice de contenidos

- [forEach](#forEach)
- [sort](#sort)
- [Obtener valor y selección de inputs](#obtener-valor-y-selección-de-inputs)
- [Obtener valor y selección de select](#obtener-valor-y-selección-de-select)
- [Fecha](#fecha)
- [Set data](#set-data)
- [Select2](#select2)
- [Buscar texto](#buscar-texto)
- [Split](#split)
- [Eliminar último caracter](#eliminar-último-caracter)
- [Replace](#replace)
- [Eliminar etiquetas HTML de un string](#eliminar-etiquetas-html-de-un-string)
- [Descargar fichero creado](#descargar-fichero-creado)
- [Leer fichero](#leer-fichero)
- [Crear objeto y cargarlo en array](#crear-objeto-y-cargarlo-en-array)
- [Temporizador](#temporizador)
- [Crear objeto](#crear-objeto)
- [JSON stringify](#JSON-stringify)

## forEach

```javascript
const array = ['this', 'is', 'a', 'test'];

array.forEach((item, index) => {

});
  
data['lineas'].forEach((lineaObtenida, index) => {
    console.log('Linea:  ' + lineaObtenida['linea'] + " Index: " + index);
});

data['lineas'].forEach(function (lineaObtenida, index) {
    console.log('Linea:  ' + lineaObtenida['linea'] + " Index: " + index);
});
            
```

## sort

```
var datosAOrdenar = data['datos'];
                    
datosAOrdenar.sort(function(a, b) {
  var dateA = new Date(a.fecha), dateB = new Date(b.fecha);
  return dateA - dateB;
});
```

## Obtener valor y selección de inputs

```
var chk_arr =  document.getElementsByName("nameInput[]");
var chklength = chk_arr.length;             

for( i = 0 ; i < chklength ; i++ )
{
    console.log(chk_arr[i].value + " - " +chk_arr[i].checked);
}
```

## Obtener valor y selección de select

```
var itemsSeleccionados = '';
    for ( var i = 0 ; i < items.options.length ; i++) {
       if ( items.options[i].selected ) {
           if (items.options[i].value != 0) {
               itemsSeleccionados += items.options[i].value + "|";
           }
       }
    }
```

## Fecha

```
var dt = new Date('2019-5-8');
var date = dt.getDate();
var month = dt.getMonth() + 1;
var year = dt.getFullYear();
if (month.toString().length == 1) {
    month = "0" + month
}
if (date.toString().length == 1) {
    date = "0" + date
}

var result = year.toString() + "-" + month.toString() + "-" + date.toString();
```

```
<input list="fechas" type="date" name="fecha" id="fecha">
    <datalist id="fechas">
      <option value="2019-01-01">
      <option value="2019-02-02">
      <option value="2019-03-03">
      <option value="2019-04-04">
      <option value="2019-05-05">
      <option value="2019-06-06">
    </datalist>
```

## Set data

```
<button id="item" type="button" data-book="2">Book</button> 

var item = document.getElementById('item');
var data = item.getAttribute("data-book");
console.log("Book: " + data);
item.dataset.book = "Julio Verne";
data = item.getAttribute("data-book");
console.log("Book: " + data);
```

## Select2

```
<select class="js-select2">
  <option value="1">Valor</option>
    ...
  <option value="20">Valor</option>
</select>

$(document).ready(function() {
    $('.js-select2').select2();
});
```

## Buscar texto

```
var str = "Buscar texto";
var n = str.includes("texto");
```

## Split

```
var str = "El veloz murciélago hindú";
var res = str.split(" ");
```

## Eliminar último caracter

```
var line = lines.slice(1, -1); 
```

## Replace

```
var str = "El veloz murciélago hindú"
var res = str.replace("hindú", "");
```

## Eliminar etiquetas HTML de un string

```
var contenido = "<p>Hello, <b>World</b>";
var texto = $(contenido).text();
```

## Descargar fichero creado

```
<script>
    
function download(text, name, type) {
  var a = document.getElementById("a");
  var file = new Blob([text], {type: type});
  a.href = URL.createObjectURL(file);
  a.download = name;
}

</script>

<a href="" id="a">click here to download your file</a>
<button onclick="download('file text', 'myfilename.txt', 'text/plain')">Create file</button>
```

## Leer fichero

```
<input type="file" id="myFile">
<hr>
<textarea style="width:100%;height: 400px" id="output"></textarea>

<script>

document.getElementById("myFile").addEventListener("change", leer);

function leer() {
    
    if (this.files && this.files[0]) {
        
        var output = document.getElementById("output");
        var myFile = this.files[0];
        var reader = new FileReader();

        reader.addEventListener('load', function (e) {
        
          output.textContent = e.target.result;
          
        });

        reader.readAsBinaryString(myFile);
        
    } 
    
}

</script>
```

## Crear objeto y cargarlo en array

```
var cursos = [];
var curso = {
  'name': 'Nombre del curso 001',
  'owner': 'Propietario 001',
}
cursos.push(curso);

var curso = {
  'name': 'Nombre del curso 002',
  'owner': 'Propietario 002',
}
cursos.push(curso);
```

## Temporizador

```
for(let i = 0; i < lines.length; i++) {

    let id = lines[i];

    setTimeout(function(){

        console.log("ID: " + id);
        execute(id);

    }, 6000 * (i+1));
       
}
```

## Crear objeto

```
var datos = new Object();
datos.id = id;
datos.valor = value;
```

## JSON stringify

```
console.log(JSON.stringify(objeto));
```
