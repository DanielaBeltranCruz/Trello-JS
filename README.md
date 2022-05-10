# 💠 API REST Trello

Práctica para jugar con la API REST de Trello. 

Consulta aquí [API REST Trello](https://github.com/LaunchX-InnovaccionVirtual/MissionNodeJS/blob/main/semanas/semana_4/6_api_rest_trello.md)


## Peticiones armadas de postman: Crear un tablero

+ Ve a la petición `POST Create Board` para crear un board.

1. En la sección de `params`, llenar los valores (aquí incluye el api key en el campo `key` y el token en `token`):

![POST Create board](https://github.com/DanielaBeltranCruz/Trello-JS/blob/master/images/api_rest_trello_1.PNG)

2. Dar clic en `Send`, mira el response y verifica que el tablero nuevo se haya creado.

![Tablero creado](https://github.com/DanielaBeltranCruz/Trello-JS/blob/master/images/api_rest_trello_2.PNG)

3. Del response, hay un campo `id` que corresponde al ID del tablero que se acaba de crear, guárdalo.

## Peticiones armadas de postman: Obtener la lista de columnas del board creado

+ Abre el request `Get Lists of Cards by Board ID.

1. Agrega el API KEY y el TOKEN.
2. Modifica la url, justo después de `/1/boards/` quita el valor que esta ahí y pon el ID del board creado anteriormente.

`https://api.trello.com/1/boards/BOARDID/lists?key=APIKEY&token=TOKEN`

3. Envía el request, y verifica la información que recibes. Deberás ver la lista de columnas que tienes en tu tablero:

![GET Lists](https://github.com/DanielaBeltranCruz/Trello-JS/blob/master/images/api_rest_trello_3.PNG)

## Peticiones armadas de postman: Agregar nuevas cards a la primer columna del tablero

+ Abre el request `POST Create Card By List Id`. 

1. Agrega los parámetros necesarios: `idList` (el id de la primer columna del paso anterior), `key`, `token`, y `name` (este es el título de la card nueva).

![POST Create Card](https://github.com/DanielaBeltranCruz/Trello-JS/blob/master/images/api_rest_trello_4.PNG)

2. Envía tu request y verifica que la respuesta sea éxitosa. Verifica que efectivamente se haya creado directo en la app de trello.

![Tablero](https://github.com/DanielaBeltranCruz/Trello-JS/blob/master/images/api_rest_trello_5.PNG)

![Tablero](https://github.com/DanielaBeltranCruz/Trello-JS/blob/master/images/api_rest_trello_6.PNG)


⭐