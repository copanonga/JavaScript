
# Snippets para JavaScript

## Índice de contenidos

- [forEach](#forEach)
- [sort](#sort)
- [Obtener valor y selección de inputs](#obtener-valor-y-selección-de-inputs)
- [Fecha](#fecha)

## forEach

```javascript
const array = ['this', 'is', 'a', 'test'];

array.forEach((item, index) => {

});
```

## sort

```var datosAOrdenar = data['datos'];
                    
datosAOrdenar.sort(function(a, b) {
  var dateA = new Date(a.fecha), dateB = new Date(b.fecha);
  return dateA - dateB;
});
```

## Obtener valor y selección de inputs

```var chk_arr =  document.getElementsByName("nameInput[]");
var chklength = chk_arr.length;             

for( i = 0 ; i < chklength ; i++ )
{
    console.log(chk_arr[i].value + " - " +chk_arr[i].checked);
}
```
## Fecha

```var dt = new Date('2019-5-8');
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
