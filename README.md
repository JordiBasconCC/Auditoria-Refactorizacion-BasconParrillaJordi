# Auditoría ASG y Refactorización Sostenible

## Fase 1: Inventario y Dimensión Ambiental (A)

[ ENLACE A LA WEB DE SMOKEDBURGUER ](https://smokedburger.es/)

Según la web [*Website Carbon Calculator*](https://www.websitecarbon.com/) , mi empresa elegida *(Smoked Burger Arahal)* está en la calificación de carbono **A**.

<img width="534" height="218" alt="image" src="https://github.com/user-attachments/assets/d42d3d02-727d-4b60-960f-0e6666d98c7e" />

Aunque está bastante bien (mejor que el 85% de todas las webs a nivel mundial como indica la misma web) puede mejorarse y llegar a un 90% o incluso más. Para ello más adelante refactorizaremos el código para conseguir un A+ y aumentar ese porcentaje.

Viendo la herramienta de desarrollador de google he podido apreciar algunos elementos de la web que tienen un mayor peso al abrir e interactuar con la web, son los siguientes:

> 1.- Imágenes en el apartado de Carta: las imágenes en el apartado del menú están siempre cargadas y no están en un formato correcto ya que se encuentran en jpg.
>
> 2.- Video de fondo: al abrir la web se puede observar un video que se reproduce nada más abrir la web, en búcle y cargado continuamente.
>
> 3.- Script de seguimiento: Tiene un peso elevado. Es una librería externa que se descarga automáticamente y añade peticiones innecesarias.

### ¿Sufre la web de "inflación de software"?
Sí, en mi opinión sufre en parte de esta inflación. Aunque la estructura de la web es limpia, meter un vídeo tan pesado en bucle solo para "decorar" la pantalla principal satura la red del usuario sin que realmente aporte una funcionalidad vital para pedir una hamburguesa.

## Fase 2: Dimensión Social y Equidad (S)

Realizaremos un test de accesibilidad desde la propia herramienta que nos proporciona google para comprobar cómo tan accesible es a personas con alguna discapacidad.

Desde ordenador / Desde móvil

<img width="473" height="198" alt="image" src="https://github.com/user-attachments/assets/f815ac03-6841-4399-80da-50ca84e7f0ac" />

En el caso de esta web, como podemos observar, es bastante accesible tanto en móvil como en sobremesa pero sigue teniendo algunos inconvenientes notables según las pautas WCAG 2.2 que mencionaré a continuación:

>1.- Falta de textos alternativos (Criterio WCAG 1.1.1): algunas de las imágenes de la carta no tienen la etiqueta alt. Esto hace que los softwares lectores de pantalla que usan las personas con discapacidad visual completa no puedan leerles los nombres de los productos ni los precios, dejándolas sin saber qué se ofrece en la web
>
>2.- Contraste de color insuficiente (Criterio WCAG 1.4.3): hay algunos textos, imágenes y botones promocionales que no se diferencian lo suficientemente bien del fondo oscuro. Esto dificulta mucho que las personas con discapacidad visual reducida puedan distinguirlos correctamente.

<img width="213" height="56" alt="image" src="https://github.com/user-attachments/assets/650e9958-1cf2-472b-a08a-946323547f5c" />

## Fase 3: Dimensión de Gobernanza y Ética (G)

Para la parte de aceptar las cookies en la web se ve muy bien la “notificación” ya que sale en colores importantes y en gran tamaño en la parte inferior de la web para así poder aceptarlas o rechazarlas sin problema alguno. 

No usa patrones oscuros para engañar o forzar al usuario a aceptarlas. El fondo es un color negro mientras que el botón es un color anaranjado como se muestra en la imagen, manteniendo una simetría visual justa:

<img width="538" height="71" alt="image" src="https://github.com/user-attachments/assets/828727b4-7ebd-4bb3-84a4-b86ab619b7a5" />

En el caso de esta web no tiene un formulario como tal, a la hora de contactar con ellos únicamente disponen de su número de teléfono, correo electrónico y dirección como se ve en la imagen:

<img width="458" height="373" alt="image" src="https://github.com/user-attachments/assets/8a1bdd90-b2bc-4612-95e6-e7998ee46b1f" />

Entonces en este caso la web no pide ningún dato al usuario, cumpliendo perfectamente con la minimización de datos que pide el RGPD de forma nativa.

## Fase 4: Propuesta de Refactorización (Green Coding)

No nos quedaremos únicamente en encontrar errores de optimización y transparencia, debemos darles solución, por lo que a continuación dejo algunas propuestas:

### 1.- Optimización de los archivos
> Como se comentó antes, las imágenes estaban en formato .jpg que no es el más adecuado para webs, así que todas las imágenes las se convertirán a WebP ya que ofrece una mayor compresión de los mismos archivos reduciendo así el peso de las imágenes entre un 25% y un 35% sin perder nada de calidad, con eso se ofrece una mejor experiencia al usuario y se da velocidad a la web (sobre todo se notará en dispositivos móviles).
> Para los videos (como el que se vé nada más entrar a la web) se utilizará MP4 con códec H.264 ya que tiene un gran equilibrio entre calidad y peso del archivo. Siendo compatible a nivel mundial con todos los navegadores.

> En este caso, la web cuenta con numerosos recursos gráficos como imágenes o videos, entonces, para aliviar peso de la web, se podría implementar Lazy Loading (carga lenta), la cual carga los archivos únicamente cuando son necesarios, mejorando el rendimiento de la web


### Reducción de peticiones

> En esta web se utiliza google analytics, lo cual se eliminaría ya que si no analizas activamente el “tráfico” de la web no es una herramienta que necesites en la web. En el caso de necesitarlo se podría buscar otra opción más liviana como plausible.

> Además utiliza google fonts, que podría eliminarse fácilmente y utilizar css para dar el estilo necesario al texto.

> También se puede observar una gran cantidad de etiquetas de redes sociales, estas no afectan directamente al rendimiento pero son innecesarias así que podrían eliminarse

### Reflexión sobre la Paradoja de Jevons.

Como dice la paradoja de Jevons, al optimizar la web y cargar mucho más rápido podríamos atraer a muchos más usuarios. Para que este éxito no anule el ahorro energético que conseguimos con las modificaciones anteriores podemos adoptar algunos habitos como pueden ser:

> Establecer un límite de peso, por ejemplo 500kb, si la web supera ese peso al añadir una nueva funcionalidad estáis obligados a optimizarla para no pasarte del límite establecido.

> En vez de que la web se cargue para cada usuario podemos utilizar generadores de sitios estáticos, que generan un archivo. Cuando un usuario intenta entrar a la web se le proporciona este archivo y así no cargamos la web.

> También debemos evitar el scroll infinito y refrescos de la página automáticos, haciendo que no genere peticiones extra.

## Fase 4: Propuesta de refactorización

Comenzando con la refactorización, en la carpeta /html existe un archivo llamado "webAntes.html" donde se puede ver el código de la web tal y como se encuentra justo antes de comenzar la refactorización.

[Ver Archivo](/html/antes/index.html)

Para con la refactorización de la web de SmokedBurguer se separará el código css del html principal en dos archivos diferentes para disminuir la carga de la web.

Siguiendo con ello se optimizarán las imagenes ya que se encuentran en jpg, siendo un formato pésimo para web, se convertirán en .webp para así ser menos pesadas y mejores para la web. Además de esto se añadirá la carga lenta de las propias imágenes para que únicamente se carguen las imágenes visibles en ese momento en la web.

Existen partes del código que en ningún momento se utilizan o que pueden ser sustituidas por alguna opción menos pesada para aumentar la velocidad de la web. Para ello el código ha sido revisado por completo y se ha ido eliminando todas estas funciones inservibles o ineficientes.

Antes de finalizar cambiaremos el código para utilizar html semántico, mejorar la privacidad y mejorar la accesibilidad y la navegación.

Comentar por ultimo que el código de la web ya venía bastante bien comentado y con nombres muy explicativos de cada parte del mismo, lo que ayuda mucho a los técnico a la refactorización y modificación del código.

Además como un detalle que es notorio en el código separé los scripts json a otro archivo por separado al igual que el css (como mencioné anteriormente)

Se a decidido separar los archivos ya que cuando un usuario visite la web, descarga el HTML, el CSS y el JSON. Si el CSS y el JSON están en archivos separados del propio html, el navegador los guarda en su caché. La próxima vez que el usuario navegue por tu sitio, no tendrá que volver a descargarlos, lo que hace que la página cargue notablemente más rápido.

Para ver el código refactorizado pulse [aquí](/html/refactorizado/index.html).
Además se incluyen algunas imagenes de la web a continuación para ver el resultado final:

<img width="830" height="531" alt="image" src="https://github.com/user-attachments/assets/808d52ba-1e39-4f9a-a5a0-af9def81e63c" />
<img width="1433" height="549" alt="image" src="https://github.com/user-attachments/assets/423400cc-7c97-4820-a76b-23dda1a2772c" />
<img width="1459" height="573" alt="image" src="https://github.com/user-attachments/assets/3a5ea3dc-a11d-47e9-a007-ed2244a7e38c" />

Ahora después de finalizar todo el proceso se realizará un test para ver la calidad de la web al igual que se realizó al inicio de la refactorización con la web inicial:

<img width="381" height="829" alt="image" src="https://github.com/user-attachments/assets/8fcf5c31-340b-4824-8de1-3994007fbb00" />

Se puede observar una alerta por un enlace redundante, por lo demás está perfecto.

## Licencias

### Visual Studio Code
Visual Studio Code cuenta con una licencia MIT (licencia de software de codigo abierto más permisiva).

### Citas

S. SmokedBurguer, "Smoked Burguer", SmokedBurguer, . [Online]. Available: https://smokedburger.es/. [Accessed: 05-20-2026].

W. Willman Acosta, "Refactorización", Willman Acosta, . [Online]. Available: https://docs.google.com/document/d/1G209kpkvMFlEUbU4CH87hF10F0nqILof_LzvSATLxz0/edit?tab=t.0#heading=h.nvj08m9tbkbp. [Accessed: 05-20-2026].

W. Willman Acosta, "Refactorización", Willman Acosta, . [Online]. Available: https://docs.google.com/presentation/d/1q1MxN1yE7uEJoiqfQjaMLDGNsylx9sLR78S7YVA0CNM/edit?slide=id.p2#slide=id.p2. [Accessed: 05-20-2026].
