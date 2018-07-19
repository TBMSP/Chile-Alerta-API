Chile Alerta - Api
=============================================================
Api para consultar los eventos sismicos de Chile y el Mundo desde las bases de datos de https://chilealerta.com y https://sismologia.net

## Funcionamiento

Es simple, utilizando la solicitud GET a https://chilealerta.com/api/query este devolverá los resultados correspondientes.

**Request**
**Syntax**
La busqueda de los eventos tiene la siguente forma:
```
https://chilealerta.com/api/query/?{parametros}
```

##Parametros
------------------------------------
**select**:
El parametro "select" es el principal para realizar la busqueda de los eventos. Este parametro puede tener las siguientes formas:
```
https://chilealerta.com/api/query/?select=ultimos_sismos //Ultimos sismos en el Mundo
https://chilealerta.com/api/query/?select=ultimos_sismos_chile //Ultimos 15 sismos en Chile
https://chilealerta.com/api/query/?select=tsunami_chile //Ultimos 16 boletines de Tsunamis en Chile
```

##Parametros Opcionales
------------------------------------
**country**:
El parametro "country" es un parametro opcional para realizar la busqueda de los eventos de algún país en especifico. Este parametro puede tener la siguiente forma:
```
https://chilealerta.com/api/query/?select=ultimos_sismos&coutry={pais}
```

Ejemplos:
```
https://chilealerta.com/api/query/?select=ultimos_sismos&coutry=chile //Chile
https://chilealerta.com/api/query/?select=ultimos_sismos&coutry=m%C3%A9xico //México
https://chilealerta.com/api/query/?select=ultimos_sismos&coutry=per%C3%BA //Perú
```

**minmagnitude**:
El parametro "minmagnitude" es un parametro numérico opcional para realizar la busqueda de los eventos. El resultado entregara eventos con magnitud mayor o superior a este parametro. Este parametro puede tener la siguiente forma:
```
https://chilealerta.com/api/query/?select=ultimos_sismos&minmagnitude={int}
```
Ejemplos:
```
https://chilealerta.com/api/query/?select=ultimos_sismos&minmagnitude=3&country=Chile //Chile
https://chilealerta.com/api/query/?select=ultimos_sismos_chile&minmagnitude=4
https://chilealerta.com/api/query/?select=ultimos_sismos&minmagnitude=3
https://chilealerta.com/api/query/?select=ultimos_sismos&minmagnitude=5
```

**minmagnitude**:
El parametro "limit" es un parametro numérico opcional para realizar la busqueda de los eventos. El resultado entregara la cantidad de eventos según el valor de este parametro (el limite máximo es 100). Este parametro puede tener la siguiente forma:
```
https://chilealerta.com/api/query/?select=ultimos_sismos&limit={int}
```
Ejemplos:
```
https://chilealerta.com/api/query/?select=ultimos_sismos&limit=3&country=Chile //Chile
https://chilealerta.com/api/query/?select=ultimos_sismos_chile&limit=4
https://chilealerta.com/api/query/?select=ultimos_sismos&limit=3
https://chilealerta.com/api/query/?select=ultimos_sismos&limit=5
```
