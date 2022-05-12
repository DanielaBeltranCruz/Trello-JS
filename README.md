# 💠 API REST Trello

Práctica para jugar con la API REST de Trello. 

**Objetivos**

+ Explorar un API Rest de un servicio como Trello.
+ Usar [Postman](https://www.postman.com/) para probar un api rest. 

Para seguir los pasos a detalle, consulta aquí [API REST Trello](https://github.com/LaunchX-InnovaccionVirtual/MissionNodeJS/blob/main/semanas/semana_4/6_api_rest_trello.md).

<details>

<summary> ⭐ Detalles </summary>

## Peticiones armadas de postman: Crear un tablero

+ Ve a la petición `POST Create Board` para crear un board.

1. En la sección de `params`, llenar los valores (aquí incluye el api key en el campo `key` y el token en `token`):

![POST Create board](https://github.com/DanielaBeltranCruz/Trello-JS/blob/master/images/api_rest_trello_1.PNG)

2. Da clic en `Send`, mira el response y verifica que el tablero nuevo se haya creado.

![Tablero creado](https://github.com/DanielaBeltranCruz/Trello-JS/blob/master/images/api_rest_trello_2.PNG)

3. Del response, hay un campo `id` que corresponde al ID del tablero que se acaba de crear, guárdalo.

## Peticiones armadas de postman: Obtener la lista de columnas del board creado

+ Abre el request `Get Lists of Cards by Board ID`.

1. Agrega el API KEY y el TOKEN.
2. Modifica la url, justo después de `/1/boards/` quita el valor que esta ahí y pon el ID del board creado anteriormente.

```
https://api.trello.com/1/boards/BOARDID/lists?key=APIKEY&token=TOKEN
```

3. Envía el request, y verifica la información que recibes. Deberás ver la lista de columnas que tienes en tu tablero:

![GET Lists](https://github.com/DanielaBeltranCruz/Trello-JS/blob/master/images/api_rest_trello_3.PNG)

## Peticiones armadas de postman: Agregar nuevas cards a la primer columna del tablero

+ Abre el request `POST Create Card By List Id`. 

1. Agrega los parámetros necesarios: `idList` (el id de la primer columna del paso anterior), `key`, `token`, y `name` (este es el título de la card nueva).

![POST Create Card](https://github.com/DanielaBeltranCruz/Trello-JS/blob/master/images/api_rest_trello_4.PNG)

2. Envía tu request y verifica que la respuesta sea éxitosa. Verifica que efectivamente se halla creado directo en la app de trello.

![Tablero](https://github.com/DanielaBeltranCruz/Trello-JS/blob/master/images/api_rest_trello_5.PNG)

![Tablero](https://github.com/DanielaBeltranCruz/Trello-JS/blob/master/images/api_rest_trello_6.PNG)

</details>

# 💠 Trello JS

Práctica de creación de proyecto con configuración externalizada para la creación de cards nuevas en Trello.

Consulta aquí [Trello JS](https://github.com/LaunchX-InnovaccionVirtual/MissionNodeJS/blob/main/semanas/semana_4/7_trello_js.md).

<details>

<summary> ⭐ Detalles </summary>

1. Crea un nuevo proyecto de js.
2. Agrega la siguiente dependencia que nos ayudará a tener configuración externalizada:
>`npm install dotenv --save`
3. Crea un script llamado app.js con lo siguiente:
   
```js
require('dotenv').config()

if(!process.env.TOKEN && !process.env.KEY){
  throw new Error('No hay configuración con Api Key y con Token')
}
```

4. Crea un archivo `.env` en la raíz del proyecto con el siguiente contenido, agrega el API KEY y el TOKEN de trello:

```
KEY="TrelloKeyHere"
TOKEN="Trellotokenhere"
```

5. Crea el archivo `.gitignore` e ignora el archivo `.env`. Como tiene información sensible NUNCA SE VERSIONA. Si se llega a versionar algún API KEY o TOKEN a GitHub, automáticamente se deshabilitará.

> Recuerda cada vez que se clone este proyecto, se tendrá que crear ese archivo .env con el API KEY y TOKEN de Trello.

6. Agrega la dependencia de Trello: `npm install trello --save`.
7. Crea el archivo `app.js` y copia el siguiente código:

```js
require('dotenv').config()

if(!process.env.TOKEN && !process.env.KEY){
  throw new Error('No hay configuración con Api Key y con Token')
}

let Trello = require("trello");
let trello = new Trello(process.env.KEY, process.env.TOKEN);

let cardTitle = `Card Nueva ${new Date()}`

trello.addCard(cardTitle, "LaunchX Card Description", "6264e42be72d295e64f5c083",
	function (error, trelloCard) {
		if (error) {
			console.log('Could not add card:', error);
		}
		else {
			console.log('Added card:', trelloCard);
		}
	});
```

Tablero de Trello

![Tablero](https://github.com/DanielaBeltranCruz/Trello-JS/blob/master/images/api_rest_trello_7.PNG)

## 🔹 Prueba del proyecto mismo

Ve al repositorio [trello-fork](https://github.com/DanielaBeltranCruz/trello-fork). Ahí se puede encontrar una modificación que se realizó al repositorio original [trello](https://github.com/norberteder/trello), se lanzan request a trello con un script que importa localmente el proyecto.

</details>

