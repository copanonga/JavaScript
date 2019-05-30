
# Snippets para JavaScript

## Índice de contenidos

- [forEach](#forEach)
- [sort](#sort)
- [Obtener valor y selección de inputs](#obtener-valor-y-selección-de-inputs)
- [Obtener valor y selección de select](#obtener-valor-y-selección-de-select)
- [Fecha](#fecha)
- [Set data](#set-data)

## forEach

```javascript
const array = ['this', 'is', 'a', 'test'];

array.forEach((item, index) => {

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
