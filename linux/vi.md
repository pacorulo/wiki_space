### Modos de vi.
Existen tres modos o estados en vi:
* modo comando: las teclas ejecutan acciones que permiten desplazar el cursor, recorrer el archivo, ejecutar comandos de manejo del texto y salir del editor. Es el modo inicial de vi.
* modo texto o modo inserción: las teclas ingresan caracteres en el texto.
 * modo última línea o ex: las teclas se usan para escribir comandos en la última línea al final de la pantalla.

### Guía de supervivencia.
Con unos pocos comandos básicos se puede ya trabajar en vi editando y salvando un texto:
```
vi arch1  arranca en modo comando editando el archivo arch1
i         inserta texto a la izquierda del cursor
a         agrega texto a la derecha del cursor
ESC       vuelve a modo comando
x         borra el caracter bajo el cursor
dd        borra una línea
h o flecha izquierda     mueve el cursor un caracter a la izquierda
j o flecha abajo         mueve el cursor una línea hacia abajo
k o flecha arriba        mueve el cursor una línea hacia arriba
l o flecha derecha       mueve el cursor un caracter a la derecha
:w        salva el archivo (graba en disco)
:q        sale del editor (debe salvarse primero)
```
**Uso avanzado de vi**
```
Invocación de vi.
  vi
abre la ventana de edición sin abrir ningún archivo.
  vi arch1
edita el archivo arch1 si existe; si no, lo crea.
  vi arch1 arch2
edita sucesivamente los archivos arch1 y luego arch2.
  vi +45 arch1
edita el archivo arch1 posicionando el cursor en la línea 45.
  vi +$ arch1
edita el archivo arch1 posicionando el cursor al final del archivo.
  vi +/Habia arch1
edita el archivo arch1 en la primera ocurrencia de la palabra "Habia".
Cambio de modo.
comando a texto:
   teclas de inserción i I a A o O, o
   tecla de sobreescritura R.
texto a comando:
   tecla ESC.
comando a última línea:
   teclas : / ?
última línea a comando:
   tecla ENTER (al finalizar el comando), o
   tecla ESC (interrumpe el comando).
 ```
 
Confundir un modo con otro la de mayor dificultades para el manejo de vi. Puede activarse un indicador de modo escribiendo
 ```
  :set showmode
```
Esto hace aparecer una leyenda que indica si se está en modo comando o inserción.

### Modo Comando.
El editor vi, al igual que todo UNIX, diferencia mayúsculas y minúsculas. Confundir un comando en minúscula digitando uno en mayúscula suele tener consecuencias catastróficas. Se aconseja evitar sistemáticamente el uso de la traba de mayúsculas; mantener el teclado en minúsculas.
Números multiplicadores.
Muchos comandos aceptan un número multiplicador antes del comando. La acción es idéntica a invocar el comando tantas veces como indica el multiplicador. 
Ejemplos:
```
  10j
en modo comando avanza 10 líneas;
  5Y
copia 5 líneas y las retiene para luego pegar.
Ejemplos de manejo.
Los siguientes ejemplos de manejo asumen que el editor se encuentra en modo comando.

flechas       mueven el cursor (si el terminal lo permite)
h j k l       mueven el cursor (igual que las flechas)
itextoESC     inserta la palabra "texto" y vuelve a comando
x             borra el caracter sobre el cursor
dw            borra una palabra
dd            borra una línea
3dd           borra las 3 líneas siguientes
u             deshace último cambio
ZZ            graba cambios y sale de vi
:q!ENTER      sale de vi sin grabar cambios
/expresiónENTER     busca la expresión indicada
3Y            copia 3 líneas para luego pegar
:6r arch3     inserta debajo de la líne 6 el archivo arch3
```
**Movimiento del cursor**
```
flechas      mover en distintas direcciones
h o BS       una posición hacia la izquierda
l o SP       una posición hacia la derecha
k o -        una línea hacia arriba
j o +        una línea hacia abajo
$            fin de línea
0            principio de línea
1G           comienzo del archivo
G            fin del archivo
18G          línea número 18
Ctrl-G       mostrar número de línea actual
w            comienzo de la palabra siguiente
e            fin de la palabra siguiente
E            fin de la palabra siguiente antes de espacio
b            principio de la palabra anterior
^            primera palabra de la línea
%            hasta el paréntesis que aparea
H            parte superior de la pantalla
L            parte inferior de la pantalla
M            al medio de la pantalla
23|          cursor a la columna 23
```
**Control de pantalla**
```
Ctrl-f    una pantalla adelante
Ctrl-b    una pantalla atrás
Ctrl-l    redibujar la pantalla
Ctrl-d    media pantalla adelante
Ctrl-u    media pantalla atrás
```
**Ingreso en modo texto**
```
i    insertar antes del cursor
I    insertar al principio de la línea
a    insertar después del cursor
A    insertar al final de la línea
o    abrir línea debajo de la actual
O    abrir línea encima de la actual
R    sobreescribir (cambiar) texto
```
**Borrar**
```
x     borrar caracter bajo el cursor
dd    borrar línea, queda guardada
D     borrar desde cursor a fin de línea
dw    borrar desde cursor a fin de palabra
d$    borrar desde cursor a fin de línea
d0    borrar desde cursor a principio de línea
```
**Copiar y pegar**
```
Y o yy      copiar línea
P           pegar antes del cursor
p           pegar después del cursor
yw          copiar palabra
y$          copiar de cursor a fin de línea
"ayy o "aY  copiar línea en buffer llamado 'a'
'a' "ayw    copiar palabra en buffer llamado
"ap         pegar desde buffer 'a', a la derecha del cursor
"aP         pegar desde buffer 'a', a la izquierda del cursor
"bdd        borrar línea y guardar en buffer 'b'
"bdw        borrar palabra y guardar en buffer 'b'
```
**Búsqueda**
```
/str    buscar hacia adelante cadena de caracteres 'str'
?str    buscar hacia atrás cadena de caracteres 'str'
n       repetir último comando / o ?
N       repetir último comando / o ? para el otro lado
fc      buscar el siguiente caracter 'c' en la línea
Fc      buscar el anterior caracter 'c' en la línea
tc      ir al caracter anterior al siguiente 'c'
Tc      ir al caracter posterior al precedente 'c'
;       repetir el último comando f, F, t, o T
,       último comando f, F, t, o T para el otro lado
```
La cadena a buscar en / o ? , de arriba abajo y viceversa respectivamente, puede ser una expresión regular.
La acción de f, F, t y T alcanza sólo a la línea actual; si el caracter buscado no está en esa línea el cursor no se mueve.

**Reemplazo**
Estos comandos admiten multiplicadores: un número delante del comando. Al dar un comando de reemplazo el editor coloca un símbolo $ en donde termina el pedido de reemplazo. El usuario escribe normalmente, sobreescribiendo, hasta donde necesite, y sale con ESC. Estos comandos admiten multiplicadores: 3cw abre un área de reemplazo para 3 palabras.
```
c         reemplaza caracteres
cw        reemplaza palabras
C o c$    reemplaza hasta el fin de línea
c0        reemplaza desde el comienzo de línea
~         marcar con serpiente sobre una letra hace que pase de mayúscula a minúscula según la naturaleza de la letra
```
**Otros**
```
J     unir dos líneas en una
ZZ    grabar cambios si los hubo y salir
u     deshacer última acción
U     deshacer todos los cambios en una línea
```
**Modo Texto**
```
BS    borrar caracter hacia la izquierda
ESC   pasar a modo comando
```
**Modo ex o última línea**
```
:q            salir si no hubo cambios
:q!           salir sin guardar cambios
:w            guardar cambios
:w arch1      guardar cambios en archivo arch1
:wq           guardar cambios y salir
:r arch2      insertar un archivo
:e arch2      editar un nuevo archivo
:e! arch2     idem sin salvar anterior
:r! comando   insertar salida de comando
:shell        salir al shell (vuelve con exit)
```
**Mover**
```
:1    mueve a línea 1 
:15   mueve a línea 15 
:$    mueve a última línea
```
**Opciones**
```
:set                cambio de opciones 
:set nu             mostrar números de línea 
:set nonu           no mostrar números de línea 
:set showmode       mostrar modo actual de vi 
:set noshowmode     no mostrar modo actual de vi
```
**Reemplazo**
La sintaxis del comando de búsqueda y reemplazo es la siguiente:
```
  :<desde>,<hasta>s/<buscar>/<reemplazar>/g
<desde>, <hasta> indican líneas en el archivo; <buscar> y <reemplazar> son cadenas de caracteres o expresiones regulares; / es un separador, s (sustituir) y g (global) son letras de comando para el manejo de expresiones regulares.
 
 :1,$s/Martes/martes/g (o también :%s/Martes/martes/g)
cambia Martes por martes en todo el archivo.
  :.,5s/ayuda/&ndo/g
cambia ayuda por ayudando desde línea actual hasta la 5a. línea.
```
**Tipo de terminal**
vi es independiente del tipo de terminal, pero la variable de ambiente TERM debe estar fijada correctamente. Si no se conoce o no existe el tipo exacto de terminal, en la mayoría de los terminales remotos el tipo ansi da buenos resultados. Para fijar el terminal en tipo ansi, digitar
```
TERM=ansi;export TERM
```
Algunos comandos, especialmente more y a veces vi, pueden no responder bien en la terminal o el emulador que se está usando. En estos casos, puede usarse Ctrl-L para refrescar la pantalla.
  
  
**Buscar y sustituir un texto en todo el documento** (dos puntos y...):
```
%s/texto_origen/texto_nuevo/g
```

**To use vi in the command line** (on bash):
```
set -o vi
```
