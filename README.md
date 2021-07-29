
# Snippets para JavaScript

## Índice de contenidos

- [Petición AJAX](#peticion-ajax)
- [Petición AJAX JSON](#peticion-ajax-json)
- [forEach](#forEach)
- [filter](#filter)
- [indexOf](#indexOf)
- [find](#find)
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
- [Comprobar variable](#comprobar-variable)
- [Mostrar popover](#mostrar-popover)
- [Select](#select)
- [Random](#random)
- [Confirm](#confirm)
- [Toast](#toast)
- [Cerrar modal](#cerrar-modal)
- [Crear celdas](#crear-celdas)

## Petición AJAX JSON

Javascript

```
var dato1 = 'Primer dato';
var dato2 = 'Segundo dato';
var success = 1;

var jsonAEnviar = {dato1, dato2, 'bloque':[], success};

for (i = 0 ; i < 3; i ++) {

var bloqueCreado = { id:i, 
doble:i+i};
jsonAEnviar.bloque.push(bloqueCreado);

}

console.log("JSON creado: " + jsonAEnviar);
jsonString = JSON.stringify(jsonAEnviar);
console.log("JSON creado string: " + jsonString);

$.ajax(
  {
    type: 'POST',
    url: 'demojson.php',
    data: {json: JSON.stringify( jsonAEnviar )},
    dataType: 'json'
  })
    .done(function(data) {

        console.log("Datos: " + JSON.stringify(data));

        if(data['success']==0) {
            console.log("Error: success " + data['success']);
        } else {

            console.log("Success");
            console.log("Mostrar dato1: " + data['dato1']);
            console.log("Mostrar dato2: " + data['dato2']);
            console.log("Mostrar bloque: " + data['bloque']);

            for ( i = 0 ; i < data['bloque'].length ; i++) {

                var bloqueObtenido = data['bloque'][i];

                console.log("ID: " + bloqueObtenido['id']);
                console.log("Doble: " + bloqueObtenido['doble']);

            }

            alert('Mostrar dato 1: ' + data['dato1'] + ' -|- Mostrar dato 2: ' + data['dato2']);

        }

    })
    .fail(function(data) {
        console.log("Error: peticionAJAXenviandoJSON");
    })
    .always(function(data) {
        console.log("Completada peticionAJAXenviandoJSON");
    });
```

Fichero demojson.php

```
<?php

if (isset($_POST['json'])) {

  $response = array();

  $data['myRequest'] =$_REQUEST;
  $total = json_decode($data['myRequest']['json'],true);

  $response["dato1"] = $total['dato1'];
  $response["dato2"] = $total['dato2'];

  $response["bloque"] = $total['bloque'];

  $response["success"] = 1;

  echo json_encode($response);

} else {

  $response = array();
  $response["success"] = 0;

  echo json_encode($response);

}
```

## Petición AJAX

Javascript

```
var datosAEnviar = [];
var datoAGuardar = { 
  id: 1
};
datosAEnviar.push(datoAGuardar);

var datoAGuardar = { 
  id: 2
};
datosAEnviar.push(datoAGuardar);

$.ajax(
      {
        url : "demopost.php",
        type: "POST",
        data : {
                dato1: 'Primer dato',
                dato2: 'Segundo dato',
                datosAEnviar: JSON.stringify(datosAEnviar)
                },
        beforeSend : function (){

        }
      })
        .done(function(data) {

            console.log("Datos: " + data);
            var mostrarData= JSON.parse(data);

            if(mostrarData['success']==0) {
                console.log("Error: success " + mostrarData['success']);
            } else {

                console.log("Success");
                console.log("Mostrar dato1: " + mostrarData['dato1']);
                console.log("Mostrar dato2: " + mostrarData['dato2']);
                alert('Mostrar dato 1: ' + mostrarData['dato1'] + ' -|- Mostrar dato 2: ' + mostrarData['dato2']);

            }

        })
        .fail(function(data) {
            console.log("Error: peticionAJAX");
        })
        .always(function(data) {
            console.log("Completada peticionAJAX");
        });
```

Fichero demopost.php

```
<?php

    if (isset($_POST['dato1']) && $_POST['dato2']) {

        $response = array();
        $response["dato1"] = $_POST['dato1'];
        $response["dato2"] = $_POST['dato2'];
        
        $datosAGuardarOriginal = $data['myRequest']['datosAEnviar'];        
        $datosAGuardar = json_decode($datosAGuardarOriginal,true);
        
        foreach ($datosAGuardar as $dato) {
          //$dato['id'];
        }
        
        $response["success"] = 1;
        
        echo json_encode($response);
        
    } else {
        
        $response = array();
        $response["success"] = 0;
        
        echo json_encode($response);
        
    }
```

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

## filter

```j
const array = ['a', 'b', 'c', 'd'];

const set = array.filter(function(item) {
  console.log()'Item: ', item);
  return item.length > 'b';
  
});

console.log(set); // c, d
```

## indexOf

```j
const array = ['a', 'bbb', 'c', 'test'];

console.log(array.indexOf('a)); // 0
console.log(array.indexOf('d)); // -1
```

## find

```j
const array = ['a', 'bbb', 'c', 'test'];

const found = array.find(function(item) {

  return item.length > 1;
  
});

console.log(found); // bbb, test         
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
Ver datos seleccionados al cambiar
```
    var eventSelect = $(".js-example-basic-multiple");
    eventSelect.select2();
    eventSelect.on("change", function (e) { 
        
        console.log("Val: " + $(".js-example-basic-multiple").select2("val"));
        console.log("Data: " + JSON.stringify(eventSelect.select2('data')));
        
        var datosObtenidos = eventSelect.select2('data');
        datosObtenidos.forEach(function (datoObtenido, index) {
            console.log('ID:  ' + datoObtenido['id'] + " Text: " + datoObtenido['text']);            
        });
    
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

function Person (firstName, lastName) {
  this.firstName = firstName,
  this.lastName = lastName
}

let person = new Person('Nombre','Apellido);

let propiedad = 'firstName';

console.log(person[propiedad]);

```

## JSON stringify

```
console.log(JSON.stringify(objeto));
```

## Comprobar variable

Comprobar si la variable es emtpy, null o undefined

```
if (!str || 0 === str.length) {...}
```

## Mostrar popover

```
<label id="miElemento"        
       data-toggle="popover"
       data-trigger="hover"
       title="Título del elemento" 
       data-original-title="Título del elemento"
       data-content="Contenido del elemento">
       
<script>
  $(document).ready(function(){
    $('[data-toggle="popover"]').popover();
  });
</script>
```

## Select

```
//Vaciar select
$('#select').empty();

//Añadir opciones al select
var selectMostrar = document.getElementById("select");
var option = document.createElement("option");
option.value = 1;
option.text = 'Dato 001';
selectMostrar.add(option);
```

## Random

```
Math.random();    //Devuelve por ejemplo: 0.8160879771995637
Math.floor(Math.random() * 11);      // Devuelve un número entre 0 y 10
Math.floor(Math.random() * 10) + 1;  // Devuelve un número entre 1 y 10
```

## Confirm

```
var resultado = confirm("¿Quieres borrar el dato?");
if (resultado == true) {
  console.log('Borrar');
} else {
  console.log('No borrar');
}
```

## Toast

```
<link rel="stylesheet" href="/rutaDelTheme/template/vendors/jquery-toast-plugin/jquery.toast.min.css">
<script src="/rutaDelTheme/template/vendors/jquery-toast-plugin/jquery.toast.min.js"></script>

$.toast({
    heading: 'Título',
    text: 'Lorem ipsum...',
    showHideTransition: 'slide',
    icon: 'info',
    loaderBg: '#46c35f',
    position: 'top-right',
    hideAfter: 6000
});

```

## Cerrar modal

```
  $("#modal").on('hidden.bs.modal', function () {
        location.reload();
  });
```


## Crear celdas

```
  ...
  <tbody id="tablaAModificar">
  ...
  
  var table = document.getElementById("tablaAModificar");

  var row = table.insertRow();

  var celda1 = row.insertCell();
  celda1.innerHTML = 'Pomelo';

  var celda2 = row.insertCell();
  celda2.innerHTML = 'pomelo@producto.es'
```
