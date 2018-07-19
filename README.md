Chile Alerta - Api
=============================================================
<center><br><img src="http://chilealerta.com/web/resources/icons/icon256.png"><br></center>
Api para consultar los eventos sismicos de Chile y el Mundo desde las bases de datos de https://chilealerta.com y https://sismologia.net <br /><br />
Los datos son los mismos que utiliza la App "Chile Alerta" para Android: https://play.google.com/store/apps/details?id=net.TBMSP.Tool.ChileAlerta <br />

# Funcionamiento

Es simple, utilizando la solicitud GET a https://chilealerta.com/api/query este devolverá los resultados correspondientes en formato JSON.<br />
El limite de la Api es de una consulta por minuto por cada usuario, por lo que es recomendable almacenar estos datos en algún archivo local para procesarlos despues.<br />
Para registrar un nuevo usuario se tiene que ingresar al siguiente formulario: https://chilealerta.com/servicios

**Request**<br />
**Syntax**<br />
La busqueda de los eventos tiene la siguente forma:
```
https://chilealerta.com/api/query/?{parametros}
```

# ¿Que información se puede obtener?
------------------------------------

La información que entregara esta API son:<br>
- Ultimos Sismos en Chile.<br>
- Ultimos Sismos en el Mundo.<br>
- Ultimos Sismos de algun país.<br>
- Ultimos Boletines de Tsunami de Chile.<br>

# Parametros
------------------------------------
**user**:<br />
El parametro "user" es el principal para realizar la busqueda de los eventos y un parametro obligatorio. Este parametro funciona como identificacion para el uso de esta Api. Ejemplo de este parametro:
```
https://chilealerta.com/api/query/?user=demo
```

**select**:<br />
El parametro "select" es uno de los principales para realizar la busqueda de los eventos y un parametro obligatorio. Este parametro puede tener las siguientes formas:
```
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos //Ultimos sismos en el Mundo
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos_chile //Ultimos 15 sismos en Chile
https://chilealerta.com/api/query/?user=demo&select=tsunami_chile //Ultimos 16 boletines de Tsunamis en Chile
```

# Parametros Opcionales
------------------------------------
**country**:<br />
El parametro "country" es un parametro opcional para realizar la busqueda de los eventos de algún país en especifico. Este parametro puede tener la siguiente forma:
```
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos&coutry={pais}
```

Ejemplos:
```
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos&country=chile //Chile
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos&country=m%C3%A9xico //México
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos&country=per%C3%BA //Perú
```

**minmagnitude**:<br />
El parametro "minmagnitude" es un parametro numérico opcional para realizar la busqueda de los eventos. El resultado entregara eventos con magnitud mayor o superior a este parametro. Este parametro puede tener la siguiente forma:
```
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos&minmagnitude={int}
```
Ejemplos:
```
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos&minmagnitude=3&country=Chile //Chile
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos_chile&minmagnitude=4
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos&minmagnitude=3
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos&minmagnitude=5
```

**limit**:<br />
El parametro "limit" es un parametro numérico opcional para realizar la busqueda de los eventos. El resultado entregara la cantidad de eventos según el valor de este parametro (el limite máximo es 100). Este parametro puede tener la siguiente forma:
```
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos&limit={int}
```
Ejemplos:
```
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos&limit=3&country=Chile //Chile
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos_chile&limit=4
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos&limit=3
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos&limit=5
```

# Ejemplo de Consulta
------------------------------------

Consulta:<br />

```
https://chilealerta.com/api/query/?user=demo&select=ultimos_sismos&limit=3&country=Chile
```


Resultado en JSON:<br />

```
{
   "metadata":{
      "request":"https:\/\/chilealerta.com\/api\/query\/?user=demo&select=ultimos_sismos&limit=3&country=Chile",
      "submitted":"2018-07-19 03:03:03 UTC",
	  "user":"demo",
      "database":[
         "Chile Alerta Database",
         "INSIMU Database"
      ],
      "version":"1",
      "select":[
         "ultimos_sismos_Chile"
      ],
      "country":"Chile",
      "limit":3,
      "minmagnitude":3
   },
   "ultimos_sismos_Chile":[
      {
         "state":1,
         "utc_time":"2018\/07\/19 00:48:02",
         "local_time":"2018-07-18 20:48:02",
         "chilean_time":"2018\/07\/18 20:48:02",
         "reference":"251 km al SE de Antofagasta - Chile",
         "magnitude":3.8,
         "scale":"Mb",
         "latitude":-24.258,
         "longitude":-68.021,
         "depth":132.15,
         "id":"56620244",
         "url":"http:\/\/sismologia.net\/?user=demo&p=detalles&id=56620244",
	 "source":"INSIMU"
      },
      {
         "state":1,
         "utc_time":"2018\/07\/18 23:34:44",
         "local_time":"2018-07-18 19:34:44",
         "chilean_time":"2018\/07\/18 19:34:44",
         "reference":"198 km al SE de Iquique - Chile",
         "magnitude":3.1,
         "scale":"Mb",
         "latitude":-21.4005,
         "longitude":-68.7295,
         "depth":121.5,
         "id":"62402836",
         "url":"http:\/\/sismologia.net\/?user=demo&p=detalles&id=62402836",
	 "source":"INSIMU"
      },
      {
         "state":1,
         "utc_time":"2018\/07\/18 23:21:58",
         "local_time":"2018-07-18 19:21:58",
         "chilean_time":"2018\/07\/18 19:21:58",
         "reference":"214 km al E de Antofagasta - Chile",
         "magnitude":4.2,
         "scale":"Mb",
         "latitude":-23.68,
         "longitude":-68.3,
         "depth":143,
         "id":"63169977",
         "url":"http:\/\/sismologia.net\/?user=demo&p=detalles&id=63169977",
	 "source":"INSIMU"
      }
   ]
}
```

<br />
Esta api no contiene información Volcánica, Meteorológica y tampoco los avisos sísmicos, alerta sísmica y alarma sísmica de la App, además esta api esta sujeta a cambios.<br /><br>Api creada por: <a href="http://twitter.com/TBMSP">@TBMSP</a> - <a href="http://twitter.com/ChileAlertaApp">@ChileAlertaApp</a><br />
<br />
