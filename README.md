# Corazones y XP Centrados
 Resourcepacks preparados para simplemente descargarlos e instalarlos con shaders vanilla (NO REQUIERE OPTIFINE) que centran los corazones y el nivel de xp.

## Tabla de contenidos
- [Corazones y XP Centrados](#corazones-y-xp-centrados)
  * [NO AUTORÍA](#no-autor-a)
  * [Descargar](#descargar)
    + [Variante normal](#variante-normal)
    + [Variante roja](#variante-roja)
  * [Instalación](#instalación)
  * [Personalización](#personalización)
    + [Color de XP](#color-de-xp)
    + [Textura de los corazones](#textura-de-los-corazones)

## NO AUTORÍA
 Estos shaders **NO fueron creados por mi**, son shaders extraidos de [este repositorio](https://github.com/McTsts/mc-core-shaders), yo solo los modifiqué y preparé ya para su uso directo.
 
## Descargar
 Hay 2 variantes listas, la variante con el color de xp por defecto, y el otro es modificado con un color rojo.

### Variante normal

 #### Versiones anteriores a la 1.19.4
 Lo puedes descargar de [***aquí***](https://github.com/Julioxidop/Corazones-y-XP-Centrados/releases/tag/normal)
 
 #### Versión 1.19.4
  Lo puedes descargar de [***aquí***](https://github.com/Julioxidop/Corazones-y-XP-Centrados/releases/tag/normal1.19.4)
 
 
 ![normal](https://i.imgur.com/NL4oUN4.png "normal")
 
 ### Variante roja
 
 #### Versiones anteriores a la 1.19.4
 Lo puedes descargar de [***aquí***](https://github.com/Julioxidop/Corazones-y-XP-Centrados/releases/tag/roja)
 
 #### Versión 1.19.4
  Lo puedes descargar de [***aquí***](https://github.com/Julioxidop/Corazones-y-XP-Centrados/releases/tag/roja1.19.4)

 
 
 ![normal](https://i.imgur.com/ASaZLi1.png "normal")

## Instalación
 Una vez descargado el resourcepack, basta con dirigirnos a nuestra carpeta de **resourcepacks** y descomprimir los archivos .rar

## Personalización
 ### Color de XP
 Para cambiar el color de la xp a nuestra necesidades tendremos que descargar la **variante roja**, luego dirigirnos al archivo `rendertype_text.vsh` ubicado en `CorazonesXPRojo\assets\minecraft\shaders\core` y abrirlo con algún editor de texto. Luego ubicar las lineas 55 y 57 donde tendremos los vec4 de los colores:
- La línea 55 es el vec4 del color del borde del texto del nivel de XP `vertexColor = vec4(0.3137, 0.0392, 0.0784, 0.9);`
- La línea 57 es el vec4 del color del relleno del texto del nivel de XP `vertexColor = vec4(0.9058, 0.2137, 0.3117, 1);`
 
 Para modificar los colores primero deberémos de tomar en cuenta que representa este vec4:
- El primer valor representa el valor del 0 al 1 del canal ROJO, es decir, cuanto rojo tiene el color en el componente RGB.
- El segundo valor representa el valor del 0 al 1 del canal VERDE, es decir, cuanto verde tiene el color en el componente RGB.
- El tercer valor representa el valor del 0 al 1 del canal AZUL, es decir, cuanto azul tiene el color en el componente RGB.
- El cuarto valor representa el valor del 0 al 1 del canal ALPHA, es decir, que tan transparente será el color.


Ahora con esto en cuenta, ahora si podemos comenzar a modificar estos valores, lo voy a explicar con un ejemplo:
Si yo quiero tener este color del relleno, primero debo de con ayuda de alguna pagina o software, checar sus componentes RGB (Yo estoy usando paint)

![color](https://i.imgur.com/N7qgrkB.png)

Ahora debo de hacer un calculo para saber que número colocar dentro de cada valor del vec4:
```
Valor que debemos de poner = Componente / 255
```
Aquí voy a poner el calculo para los 4 valores en este ejemplo:
```
Primer valor (rojo): 255 / 255 = 1.0
Segundo valor (verde): 127 / 255 = 0.4980
Tercer valor (azul): 39 / 255 = 0.1529
```
Y para el cuarto valor por lo general no necesitamos hacer calculos, solo saber que 0 es totalmente transparente e 1 es sin transparencia, ya podemos nosotros jugar con este valor. En este ejemplo yo lo voy a dejar en 1.0

Y listo, ahora si basta con reemplazar estos valores en el vec4 de la línea 57 (O en la 55 si estamos modificando el borde):

![vec4mod](https://i.imgur.com/Pq2OvsS.png)

### Textura de los corazones
El shader a nivel interno funciona detectando un color negro con opacidad 1 (de 255) en las texturas de los corazones, por lo que si nosotros queremos usar nuestras propias texturas de los corazones, debemos de igualmente colocar este color negro de opacidad 1 en las texturas de nuestros corazones.
Voy a ilustrar como hariamos para preparar esta textura.

Primero necesitamos abrir el archivo `icons.png` ubicado en la carpeta `NAME\assets\minecraft\textures\gui` de nuestro resourcepack en algun editor de imágenes, en mi caso estaré usando ASEPRITE.

**NO RECOMIENDO PHOTOSHOP YA QUE AQUI LA OPACIDAD LA TRABAJA EN PORCENTAJES, Y NECESITAMOS EL VALOR 1 DE OPACIDAD, NO EL 1% DE OPACIDAD**

![img](https://i.imgur.com/1tgX5z7.png)

Ahora en nuestro editor de imágenes vamos a crear una nueva capa y la vamos a posicionar debajo de la capa que tiene las texturas.

![img](https://i.imgur.com/PNimOiT.png)

Ahora con el archivo abierto debemos de visualizar de que tamaño es la textura del corazón, por defecto el bounding de la textura del corazón es de 9x9, pero en algunos resourcepacks esto puede cambiar, en este ejemplo el bounding es de 9x9 (Creo que si tienes texturas que sean de mayor resolución el resourpack no funcionará)

![img](https://i.imgur.com/AIzQNHw.png)

Luego, ahora vamos a seleccionar el color negro puro, con opacidad de 1

![img](https://i.imgur.com/zoIpTYi.png) 

Toca el momento de pintar, debemos de seleccionar BIEN todo el área que abarcan los corazones, en este caso el área que estoy seleccionando va a ser de 9 de alto (el valor que checamos en el paso anterior) por 180 de ancho (9 multiplicado por 20) y luego pintar con nuestro color negro puro con opacidad de 1

![img](https://i.imgur.com/ncilb7T.png)

Y ahora hacemos esto con todas las texturas de los corazones, lo rojo en la siguiente imagen representa que es lo que debemos de pintar con el color negro opacidad 1

![img](https://i.imgur.com/pHF7TAm.png)

Y listo, solo guardamos el archivo en la carpeta!

