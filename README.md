
# Snippets para JavaScript

## Índice de contenidos

- [forEach](#forEach)
- [sort](#sort)
- [Obtener valor y selección de inputs](#Obtener valor y selección de inputs)

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

##Obtener valor y selección de inputs

```var chk_arr =  document.getElementsByName("nameInput[]");
var chklength = chk_arr.length;             

for( i = 0 ; i < chklength ; i++ )
{
    console.log(chk_arr[i].value + " - " +chk_arr[i].checked);
}
```
