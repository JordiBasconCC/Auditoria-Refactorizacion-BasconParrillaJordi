# Auditoria ASG y Refactorizacion Sostenible

## Fase 1: Inventario y Dimensión Ambiental (A)

Según la web [*Website Carbon Calculator*](https://www.websitecarbon.com/) , mi empresa elegida *(Smoked Burger Arahal)* está en la calificación de carbono **A**.

<img width="534" height="218" alt="image" src="https://github.com/user-attachments/assets/d42d3d02-727d-4b60-960f-0e6666d98c7e" />

Aunque está bastante bien (mejor que el 85% de todas las webs a nivel mundial como indica la misma web) puede mejorarse y llegar a un 90% o incluso más. Para ello más adelante refactorizar el código para conseguir un A+ y aumentar ese porcentaje.

Viendo la herramienta de desarrollador de google he podido apreciar algunos elementos de la web que tienen un mayor peso al abrir e interactuar con la web, son los siguientes:

> **1.-** Imágenes en el apartado de Carta: las imágenes en el apartado del menú están siempre cargadas y no están en un formato correcto ya que se encuentran en jpg.
> 
> **2.-** Video de fondo: al abrir la web se puede observar un video que se reproduce nada más abrir la web, en búcle y cargado continuamente.

## Fase 2: Dimensión Social y Equidad (S)

Realizaremos un test de accesibilidad desde la propia herramienta que nos proporciona google para comprobar cómo tan accesible es a personas con alguna discapacidad.

Desde ordenador / Desde móvil

<img width="473" height="198" alt="image" src="https://github.com/user-attachments/assets/f815ac03-6841-4399-80da-50ca84e7f0ac" />

En el caso de esta web, como podemos observar, es bastante accesible tanto en móvil como en sobremesa pero sigue teniendo algunos inconvenientes notables que mencionare a continuación:

> 1.- No tiene una opción para personas con discapacidad visual completa, por ejemplo, lectura de precios y nombres, sin ello estas personas no pueden saber absolutamente nada de esta web.
>
> 2.- Hay algunos textos, imágenes y botones que no se diferencian lo suficientemente bien como para que algunas personas con discapacidad visual reducida no puedan diferenciarlos del fondo o de otros elementos.

<img width="213" height="56" alt="image" src="https://github.com/user-attachments/assets/650e9958-1cf2-472b-a08a-946323547f5c" />

## Fase 3: Dimensión de Gobernanza y Ética (G)

Para la parte de aceptar las cookies en la web es muy notoria la “notificación” ya que sale en colores importantes y en gran tamaño en la parte inferior de la web para así poder aceptarlas o rechazarlas sin problema alguno.

No usa colores oscuros para forzar al usuario a aceptarlas, el fondo es un color negro mientras que el botón es un color anaranjado como se muestra en la imagen:

<img width="538" height="71" alt="image" src="https://github.com/user-attachments/assets/828727b4-7ebd-4bb3-84a4-b86ab619b7a5" />

En el caso de esta web no tiene un formulario como tal, a la hora de contactar con ellos únicamente disponen de su número de teléfono, correo electrónico y dirección como se ve en la imagen:

<img width="458" height="373" alt="image" src="https://github.com/user-attachments/assets/8a1bdd90-b2bc-4612-95e6-e7998ee46b1f" />

Entonces en mi caso la web no pide ningún dato al usuario 

## Fase 4: Propuesta de Refactorización (Green Coding)

No nos quedaremos únicamente en encontrar errores de optimización y transparencia, debemos darles solución, por lo que a continuación dejo algunas propuestas:

### 1.- Optimización de los archivos
> Como antes comenté las imágenes estaban en formato .jpg que no es el más adecuado para webs, así que todas las imágenes las convertiremos a WebP ya que ofrece una mayor compresión de los mismos archivos reduciendo así el peso de las imágenes entre un 25% y un 35% sin perder nada de calidad, con eso ofreceremos una mejor experiencia al usuario y daremos velocidad a la web (sobre todo se notará en dispositivos móviles).
> Para los videos (como el que se vé nada más entrar a la web) utilizaremos MP4 con códec H.264 ya que tiene un gran equilibrio entre calidad y peso del archivo. Siendo compatible a nivel mundial con todos los navegadores.

> En este caso, la web cuenta con numerosos recursos gráficos como imágenes o videos, entonces, para aliviar peso de la web, podríamos implementar Lazy Loading (carga lenta), la cual carga los archivos únicamente cuando son necesarios, mejorando el rendimiento de la web

### Reducción de peticiones

> En esta web se utiliza google analytics, lo cual eliminaría ya que si no analizas activamente el “tráfico” de la web. En el caso de necesitarlo podrías buscar otra opción más liviana como plausible.

> Además utiliza google fonts, que podría eliminarse fácilmente y utilizar css para dar el estilo necesario al texto.

> También se puede observar una gran cantidad de etiquetas de redes sociales, estas no afectan directamente al rendimiento pero son innecesarias así que podrían eliminarse

### Reflexión sobre la Paradoja de Jevons.

Como dice la paradoja de Jevons, al optimizar la web y cargar mucho más rápido podríamos atraer a muchos más usuarios. Para que este éxito no anule el ahorro energético que conseguimos con las modificaciones anteriores podemos adoptar algunos habitos como pueden ser:

> Establecer un límite de peso, por ejemplo 500kb, si la web supera ese peso al añadir una nueva funcionalidad estáis obligados a optimizarla para no pasarte del límite establecido.

> En vez de que la web se cargue para cada usuario podemos utilizar generadores de sitios estáticos, que generan un archivo. Cuando un usuario intenta entrar a la web se le proporciona este archivo y así no cargamos la web.

> También debemos evitar el scroll infinito y refrescos de la página automáticos, haciendo que no genere peticiones extra.

## Fase 4: Propuesta de refactorización

Comenzando con la refactorización, en la carpeta /html existe un archivo llamado "webAntes.html" donde se puede ver el código de la web tal y como se encuentra justo antes de comenzar la refactorización.

[Ver Archivo](/html/webAntes.html)

Para comenzar con la refactorización de la web de SmokedBurguer se optimizarán las imagenes ya que se encuentran en jpg, siendo un formato pésimo para web, se convertirán en .webp para así ser menos pesadas y mejores para la web. Además de esto se añadirá la carga lenta de las propias imágenes para que únicamente se carguen las imágenes visibles en ese momento en la web.

Existen partes del código que en ningún momento se utilizan o que pueden ser sustituidas por alguna opción menos pesada para aumentar la velocidad de la web. Para ello el código ha sido revisado por completo y se ha ido eliminando todas estas funciones inservibles o ineficientes.

## Licencias

### Visual Studio Code
Visual Studio Code cuenta con una licencia MIT (licencia de software de codigo abierto más permisiva).
