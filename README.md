# Corazones y XP Centrados
 Resourcepacks preparados para simplemente descargarlos e instalarlos con shaders que centran los corazones y el nivel de xp.
 
## NO AUTORÍA
 Estos shaders **NO fueron creados por mi**, son shaders extraidos de [este repositorio](https://github.com/McTsts/mc-core-shaders), yo solo los modifiqué y preparé ya para su uso directo.
 
## Descargar
 Hay 2 variantes listas, la variante con el color de xp por defecto, y el otro es modificado con un color rojo.

### Variante normal
 Lo puedes descargar de [***aquí***](https://github.com/Julioxidop/Corazones-y-XP-Centrados/releases/tag/normal)
 
 
 ![normal](https://i.imgur.com/NL4oUN4.png "normal")
 
 ### Variante roja
 Lo puedes descargar de [***aquí***](https://github.com/Julioxidop/Corazones-y-XP-Centrados/releases/tag/roja)
 
 
 ![normal](https://i.imgur.com/ASaZLi1.png "normal")

## Instalación
 Una vez descargado el resourcepack, basta con dirigirnos a nuestra carpeta de **resourcepacks** y descomprimir los archivos .rar

## Personalización
 ###Color de XP
 Para cambiar el color de la xp a nuestra necesidades tendremos que descargar la **variante roja**, luego dirigirnos al archivo `rendertype_text.vsh` ubicado en `CorazonesXPRojo\assets\minecraft\shaders\core` y abrirlo con algún editor de texto. Luego ubicar las lineas 55 y 57 donde tendremos los vec4 de los colores:
- La línea 55 es el vec4 del color del borde del texto del nivel de XP `vertexColor = vec4(0.3137, 0.0392, 0.0784, 0.9);`
- La línea 57 es el vec4 del color del relleno del texto del nivel de XP `vertexColor = vec4(0.9058, 0.2137, 0.3117, 1);`
 Para modificar los colores primero deberémos de tomar en cuenta que representa este vec4:
- El primer valor representa el valor del 0 al 1 del canal ROJO, es decir, cuanto rojo tiene el color en el componente RGBA.
- El segundo valor representa el valor del 0 al 1 del canal VERDE, es decir, cuanto verde tiene el color en el componente RGBA.
- El tercer valor representa el valor del 0 al 1 del canal AZUL, es decir, cuanto azul tiene el color en el componente RGBA.
- El cuarto valor representa el valor del 0 al 1 del canal ALPHA, es decir, que tan transparente será el color.


Ahora con esto en cuenta, ahora si podemos comenzar a modificar estos valores, lo voy a explicar con un ejemplo:
Si yo quiero tener este color del relleno, primero debo de con ayuda de alguna pagina o software, checar sus componentes RGB (Yo estoy usando paint)

![color](https://prnt.sc/lD8PpBhS-CHd)
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
Y para el cuarto valor por lo general no necesitamos hacer calculos, solo saber que 0 es totalmente transparente e 1 es sin transparencia, ya podemos nosotros jugar con este valor.

Y listo, ahora si basta con reemplazar estos valores en el vec4 de la línea 57:
![vec4mod](https://prnt.sc/1aucd0lKkfMk)

###Textura de los corazones
