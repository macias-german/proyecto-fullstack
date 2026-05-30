# README EN CONSTRUCCION.

## Objetivo del proyecto.
El objetivo final del proyecto es crear un contador de caracteres que sea capaz de diferenciar en un texto la siguiente información:


- _Cantidad total de caracteres en el texto._
- _Cantidad total de palabras en el texto._
- _Cantidad total de párrafos en el texto._
- _Cantidad total y porcentual del uso de cada letra única en el texto._


## Desarrollo y estado actual.
El proyecto sé ira desarrollando en varias faces a lo largo del tiempo, sé ira dejando una marca según el estado actual del proyecto.


- _~~Desarrollo del HTML (hardcoding).~~_
- _~~Desarrollo del CSS correspondiente.~~_
- _**Desarrollo del Javascript para funcionalidad.**_
- _En desarrollo..._


## Tecnologías utilizadas.
![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white)


- _Actualmente el proyecto utilizá únicamente HTML5 y CSS3. En vista al futuro el proyecto ira incorporando más funcionalidades y tecnologías._


## Organización del HTML.
_El HTML se organizo todo dentro de un 'section', el mismo cuenta con un header donde se ubica la informacion del sitio y luego se separo el contenido en 'div' el cual cada uno cuenta con su propia clase para identificar de que se trata cada apartado.


## Resolución del CSS.
_El CSS se realizó y organizo siguiendo el mismo orden aplicado en el HTML, se utilización comentarios para separar cada zona del proyecto, comenzando con un general donde se aplicaron los reseteos y se declararon las variables y seguido por la configuración especifica de cada section y div utilizado a lo largo del proyecto._


## Dificultades encontradas durante el desarrollo.
Durante el desarrollo no se encontraron problemas en cuanto el HTML pero si al estilizar en CSS.
Todas estas dificultades fueron solucionadas solicitando la mínima ayuda posible a un agente de inteligencia artificial.
A continuación detallaré los más importantes:


### Eliminar "resize" y "outline" del textarea.
Al momento de estilizar el textarea me encontré con el problema del "estiramiento" de la caja de forma manual y el contorno que aparecía al hacer click dentro del cuadro.

- _Con "resize: none;" se elimina la posibilidad de redimensionar el textarea manualmente._


`textarea { resize: none; }`


- _Con "textarea:focus" y "outline: none;" se le dice al textarea que cuando esté en "focus", o mejor dicho, seleccionado por el usuario el contorno llamado "outline" no sea visible._


`textarea:focus { outline: none; }`


### Crear "checkbox" personalizado.
Debido al diseño por defecto del input checkbox se dificultó la tarea de estilizarlo, por lo cual se investigó y se creó una "caja invisible" con la funcionalidad de los checkbox.


- _Con "appearance: none;" se elimina el estilo por defecto del checkbox haciéndolo "invisible" luego le defino las propiedades width, height y border para crear un "cubo" personalizado y le aplico "cursor: pointer;" para que cambie el cursor imitando el comportamiento de un input._


`input { appearance: none; width: 18px; height: 18px; border: solid 2px; cursor: pointer; }`


- _Para simular el "check" de la checkbox se le agrega ":checked" al input y se le asigna un background-color de la tonalidad requerida por el estilo._


`input:checked { background-color: var(--color); }`


### Configuraciones del "background-image".
Este fue un problema bastante simple de solucionar, pero debido a que no recordaba bien todas las propiedades del backgound-image tuve que solicitar ayuda debido a que no podía estirar la imagen correctamente y siempre se recortaba o perdía los bordes.


- _Con este código le digo a la imagen de fondo que no se repita hacia ninguno de sus lados, que esté centrada y que tenga el 100% de su tamaño tanto de alto como de ancho utilizando como 100% el tamaño del contenedor haciendo que la imagen se estire y no pierda contenido._


`.img-container { background-repeat: no-repeat; background-position: center; background-size: 100% 100%; }`


### Estilizado de las "meter".
La etiqueta "meter" trae su propio estilo por defecto el cual es algo complejo para modificar, no importaba la propiedad que se modifique los cambios nunca aplicaban.
La forma de estilizar los "meter" dependen del navegador utilizado, en mi caso utilizo el que requiere google chrome.


- _Con el 100% del width le digo que ocupe todo el ancho del contenedor disponible, en este caso como utilice grid, ocupa toda su "cajita" con la barra y el height le asigna un alto que hace visible el contenido de la barra._


`meter { width: 100%; height: 15px; }`


- _Para estilizar el "fondo" de la barra se utiliza "::-webkit-meter-bar", luego se le puede asignar el color deseado utilizando background-color._


`meter::-webkit-meter-bar { background-color: var(--color); }`


- _Para estilizar la "barra de progreso" se utiliza "::-webkit-meter-optimum-value", luego se le puede asignar el color deseado utilizando background-color._


`meter::-webkit-meter-optimum-value { background-color: var(--color); }`


### Estilizado del boton "details" y creacion de la "flecha desplegable".
La etiqueta "details" utiliza "summary" como nombre interno, por lo cual la modificación del estilo no depende completamente del "details".


- _Para eliminar "la flecha" que trae por defecto el details se elimina desde el summary._


`details summary { list-style: none; }`


- _Ahora dado que la idea era crear una flecha nueva y personalizada, para esto se utiliza el "::after" que indica que siempre que aparezca un summary dentro de un details se le va a agregar la flecha al lado. Al utilizar "content: ""; " creo un "espacio vacío" que con "display: inline-block;" me permite modificar su width y height para generar una "caja". Con border-bottom y border-right genero una "L" que luego con "transform: rotate(45deg); lo giro para simular una flecha hacia abajo._


`details summary::after { content: ""; display: inline-block; width: 5px; height: 5px; border-bottom: 2px solid var(--color); border-right: 2px solid var(--color); transform: rotate(45deg); }`


- _Para invertir la flecha creada al momento de desplegar la lista se le agrega [open] al details para darle a entender que es cuando el details esta abierto y se le agrega al "summary::after" un transform que rota 180 grados la flecha creada haciendo que la misma apunte hacia arriba_ 


`details[open] summary::after { transform: rotate(225deg); }`


### Barra scroll con espacio reservado.
Al realizar el desplegable del details me encontré con el problema de que el contenido se movía hacia arriba y hacia la izquierda, por lo cual tuve que revisar el porqué pasaba esto.


- _Al atribuirle "flex-start" al body, lo que hace es que todo el contenido se renderice directamente desde el comienzo del contenedor hijo, evitando que el contenido sea empujado hacia donde no debería._


`body { justify-content: flex-start; }`


- _Para evitar el desplazamiento por culpa de la barra de navegación de los navegadores, lo que tuve que decirle al HTML que reserve por defecto los pixeles donde se encontrara la scroll bar en caso de que aparezca alguna._


`html { scrollbar-gutter: stable; }`


### Crear simbolo "<" como texto en HTML.
Debido a que las etiquetas utilizan los simbolos " " para su sintaxis, al querer ingresar una como texto, ya sea para un título o para un párrafo la misma genera un error dentro del HTML, ya que busca crear una etiqueta.


- _Para poder generar como texto dicho símbolo se utilizó el código "lt" que significa "less than" con el símbolo & al inicio para indicarte que estamos hablando de un carácter especial._


`&lt;`


## Captura del estado actual del proyecto.
- _Muestra del estado actual del proyecto en versión de computadora._
![Imagen de muestra de la versión para computadora de Character Counter.](./preview/preview-pc.webp)