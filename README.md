# Obligatorio-DevOps
El objetivo básico de este obligatorio es hacer un script que liste los correos electrónicos contenidos en  los  archivos  regulares  de  un  directorio  pasado  como  parámetro  (con  opciones  para  buscar  los archivos,  que contienen los  correos,  en forma  recursivaa  partir  de  él,  y  poder  buscar  solamente  en los  archivos  regulares  no  ocultos  de  la  forma  \*.txt y  de  un  dominio  especifico),  y hacer  un  script  en Python  que  lo  utilice  apropiadamente  para  agregarle másfuncionalidadesy  flexibilidad  en  la interpretación de sus parámetros(agregando funcionalidadesde cuenta de correos encontrados por dominio, cantidad total de dominiosencontrados, filtrado con una expresión regular, ordenamiento del listado según distintas opciones).El obligatorio consiste en la creación de un script en bash y un script en Python.

## Bash

Realizar un scripten bash (shell script)que sea de la forma:ej1\_busca\_correos  [-r]  [-t] [-d dominio]  DirectorioEl script deberá listar todos loscorreos electrónicos (un correo por línea) encontrados en los archivos regulares del directorio pasado como parámetro, sin importar si son o no ocultos. Después del listado de  correos  electrónicos  encontrados,  el  script  deberá  desplegar  la  cantidad  de  correos  listados.
En caso  de  recibirse  el  modificador -r,  selistaránlos  correos  electrónicos detodos  los  archivos contenidos  a  partirdel  directorio  pasado  como  parámetrobuscándolosen  forma  recursiva  (la búsqueda de archivos, para obtener los correos que tengan dentro, será recursivaen la estructura de directorios  partiendo  del  parámetro Directorio).  Si  el  script  no  recibe  el  modificador -r,  solo  se tomarán en cuenta los archivos del directorio pasado como parámetro y no los de los subdirectorios (no será recursivo). Así, la búsqueda en estos archivos será recursiva o no según se reciba o no el modificador -r.En  caso  de  recibirse  el modificador -t,  el  script  deberá  buscar  direcciones  de  correo electrónico  solamente  en  los  archivos  regulares  no  ocultos  con  extensión .txt.  Si  el  script  recibe  el modificador-d,  seguidamente  a  este  modificador,  se  aceptará  un  nombre  de  dominio  para  que  el script solo desplieguedirecciones de correo electrónicode ese dominio.En caso de hacerse una búsqueda de correos recursiva (modificador -r), los subdirectorios (dentro del directorio  pasado  como parámetro)  donde  el  script  no tenga  permisos  de  acceso  para  poder  buscar en  los  archivos  que  contengan  (para  buscar  los  correos  electrónicos  en  ellos),  simplemente  se ignorarán. Este problema de acceso no se considerará que cause un error en la ejecución global del script, por lo que el código de retorno no será distinto de cero por esta razón. Los archivos regulares (o regulares no ocultos con extensión .txt) donde el script no tenga permisos lecturapara poder leer y buscar direcciones de correo electrónico también se ignorarán. En caso que exista algún archivo que no se tenga acceso a él, igualmente el código de retorno del script no será distinto de cero por esa razón.  Si  el  script tiene  los  permisos  adecuados para  poder  buscar  archivos  en  el  directorio  pasado como   parámetro,   retornará  un   0  como  código  de  retorno,   aunque   no   pueda  acceder   a   los subdirectorios  y/o  a  los  archivos  que  hay  dentro  de  ellos  o  del  mismo  directorio  pasado  como parámetro.Elscript  aceptará  tanto  un  camino  absoluto  como  relativo  al  directorio,  aunque  todos  los  caminos desplegados  siempre  serán  absolutos  (en  caso  que  tenga  que  desplegar  un  mensaje  de  error indicando el camino al directorio pasado como parámetro o en el mensajecon la cantidad de correos encontrados en los archivos de ese directorio), sin importar el tipo de camino que ha recibido. El  script  deberá  validar  la  existencia  del  directorio  pasado  como  parámetro,  verificando  que  sea  un directorio  y  que  se  tengan  lospermisos  necesarios  para  acceder  a  él.  Si  el  directorio  ingresado  no existe en el sistema de archivos, el script deberá desplegar el mensaje “El  directorio  <  camino absoluto  al  directorio  pasado  como  parámetro,  aunque  se  ingrese  un  camino  relativo  >  no existe.” por su salida estándar de errores, devolviéndose un 1 como código de retorno del script. Si el directorio  parámetro  como  parámetro  no  es  un  directorio  (es  un  archivo  de  otro  tipo),  deberá desplegarse el mensaje “El  parámetro  <  camino  absoluto  al  supuesto  directorio  pasado  como parámetro, aunque se ingrese un camino relativo > no es un directorio.” por su salida estándar de errores, devolviéndose un 2 como código de retorno del script. Si no se tienen todos los permisos adecuados en el directorio pasado como parámetro para obtener los datos necesarios y poder hacer el listado, deberá desplegarse el mensaje “No setienen los permisos necesarios para acceder al directorio  y  buscar  correos.” por la salida estándar de errores y deberá devolverse un 3 como código de retorno del script. Si el script recibe un numero incorrecto de parámetros, se deberá desplegar un mensaje de error que diga “Cantidad de parámetros incorrecta, solo se recibenlos modificadores -r, -t, -d dominio y un directorio accesible en el sistema de archivos.” por la salida estándar de errores y se deberá devolver un 4 como resultado (como código de retorno del script).
Si  se  recibe  un  modificador  inválido,  se  deberá  desplegar  el  mensaje  de  error  “Modificador  <modificador  pasado  como parámetro> incorrecto,  solo  se  acepta -r, -t  y -d.”  por  la  salida estándar de errores y se devolverá un 5 como código de retorno del script.En  caso  de  cualquier  otro  posible  error,  se  desplegará  un  mensaje  de  texto  apropiado  por  la  salida estándar de errores y se deberá retornar un 6 como resultado (como código de retorno del script).Si  no  hay  errores,  se  desplegará  por  la  salida  estándar  el  listado  de  todos  los  correos  electrónicos encontrados  seguido  del  texto  “Cantidad  de  correos  encontradosen  el  directorio  <  camino absoluto  al  directorio  pasado  como  parámetro,  aunque  se  ingrese  un  camino  relativo  >:” desplegándose  después  de  ese  texto  la  cantidad  total  de  correos  electrónicos  encontrados  y  se devolverá  un  0  como  código  de  retorno  del  script.  Los  correos  electrónicos  se  desplegarán  uno  por línea, aunque en el archivo original (de donde se obtuvieron) pudieran estar más de uno por línea. Si tampoco se producen errores, pero no hay ningún correo electrónico encontrado, se desplegará por la salida  estándar de  errores el texto “No  se  han  encontrado  correos  en  el  directorio  <  camino absoluto  al  directorio  pasado  como  parámetro,  aunque  se  ingrese  un  camino  relativo  >.” En este caso, también se retornará un 0 como código de retorno del script (no se considera un error si no hay nada para listar).Se  considerará  un  correo  electrónico  cualquier  secuencia  de  caracteres  que  se  componga  de  tres partes  seguidas.  Una  primera  parte  formada  0  o  más  caracteres  que  sean  letras  mayúsculas  o minúsculas, dígitos o los caracteres “_” y “.” (punto). Como segunda parte el carácter “@” rodeado de una  letra  o  dígito.  De  esta  manera,  tanto  antes  y  como  después  del  “@”  tiene  que  haber obligatoriamente  un  carácter  que  sea  una  letra  (mayúscula  o  minúscula)  o  un  dígito.  Como  tercera parte,  algo  muy  parecido  a  la  primera  parte:  0  o  más  caracteres  que  sean  letras  mayúsculas  o minúsculas, dígitos o los caracteres “_” y “.” (punto). El ultimo dígito de estatercerasecuencia tiene que ser una letra (mayúscula o minúscula) o un dígito, no pudiendo ser “_” ni “.” ni ninguna otra cosa (no será tomado en cuenta como parte del correo un carácter así al final). Como restricción adicional, después  del  @  tendrán  que  haber  al  menos  dos  caracteres  que  sean  letras  (mayúsculas  o minúsculas) o dígitos (no pueden ser ni “_” ni “.”).Debe considerarse como correo la secuencia más grande que contiene este patrón y no secuencias menores, así como distinguirse correctamente direcciones de correo, aunque terminen, comiencen o estén  entre  medio  de  cada  línea.  También  deberán  distinguirse  correctamente  las  direcciones  de correo, aunque se tengan varias en una misma línea.Por ejemplo, la línea siguienteEl correo de pepe es el_pepe@adinet.com.uy y el de Juanita es juanita.mengano_32@ggmail.com.xxDebe producir los correos:el_pepe@adinet.com.uyjuanita.mengano_32@ggmail.com.xxcada correo en una línea separada.Al final de la lista de correos deberá desplegarse la cantidad de correos encontrados.

## Python

El objetivo del ejercicio 2es hacer un script de Python que despliegue información producida en base a la salida del script creado en el ejercicio 1, agregándole funcionalidadesy siendo másflexible en la interpretación de los modificadores (no requiriendo un orden específicoparapoder reconocerlos).
El ejercicio 2 consiste en realizar un script en Python que sea de la forma:

ej2_busca_correos_expandido.py[-r]  [-t] [-d dom]  [-e {d,t,c}]  [-f RegExp][-o {a,d,l}]  Dir

El  script  de Python  recibirá  las  indicacionessegún  lo  ingresado  por  el  usuarioen  la  línea  de comandos (modificadores, opciones,dominio,expresión regulary directorio)y desplegaráloscorreoselectrónicosencontrados,que se encuentran en los archivos del directorio pasado como parámetro,siguiendolas  especificaciones  de  los  modificadores  y  opciones  ingresadas  por  el  usuario.El  script Python deberá aceptarlos modificadores en cualquier orden, pudiendo estar o no presentes. Tresde los modificadores del script de Python son iguales a los del ejercicio 1. Esas opciones serán tratadas de igual forma a ese script (-rparauna búsqueda delos correos electrónicos en los archivos contenidos a partir del directorioDiren forma recursiva,-tparabuscar los correos solamente en los archivos  regulares  no  ocultos  con  extensión .txty -d,  seguido  de  un  dominio,  para  desplegar  los correos solo de ese dominio, se interpretarántambiénasípara la funcionalidad extendida del script en Python).A las mismas opciones que tiene el script en bash del ejercicio 1, el script de Python le agrega másfuncionalidades dadas por los siguientes modificadores:Si  el  script  en  Python  recibe  el  modificador -h,  desplegará  una  ayuda  (por  la  salida  estándar) explicando para qué sirven los diferentes modificadores y la sintaxis general del comando. Si  el  script  en  Python  recibe  el  modificador -e,  desplegará(después  del  listado  de  correos electrónicos)la  cantidad  de  correos encontradospor  dominio  y/ola  cantidad  dedominios  diferentesencontrados,según la opción dada por el usuario. Si se recibe dcomo parámetro de la opción -e(el usuario  ingresa  en  la  línea  de  comandos -ed),  entonces  se  desplegaráunel  listadoindicando  la cantidad de correos para cada dominio encontrado, y antes de ese listado el texto “Reporte cantidad de  correos  encontrados  por  dominio:”, seguido de una línea vacía, por la salida estándar. Si se recibe tcomo parámetro de la opción -e(el usuario ingresa en la línea de comandos -et), entonces se desplegaráel texto “Cantidad dedominios diferentes encontrados:”,seguido de la cantidad de dominios distintos encontrados, por la salida estándar.Si se recibe ccomo parámetro de la opción -e(el  usuario  ingresa  en  la  línea  de  comandos -ec),  entonces  se  desplegará  tanto  el  listado  dela cantidad  de  correos  por  dominio  como  la  cantidad  total  de dominios encontrados,  desplegándose primero  el  decantidad  de  correospor  dominio  y  después  la  cantidad  total  de dominios  distintos encontrados,en las mismas condiciones como si el usuario hubiera optado por la opción d(habiendo ingresado -ed),  seguidamente  una  línea  (enter)  de  separación  por  la  salida  estándar  y  despuésdesplegarsela cantidad total de dominios diferentesencontrados, en las mismas condiciones como si el usuario hubiera optado por la opción t(habiendo ingresado -et).
Si el script en Python recibe el modificador -fseguido de una expresión regular,solo se desplegarán y contabilizarán  los  correos  electrónicos  que  verifican  la expresiónregularRegExppasada  como parámetro.  Si  la  expresión  ingresada  comoparámetro  es  incorrecta  (sintácticamente  errónea),  se deberá  desplegar  un  mensaje  de  error  que  diga “La expresiónregular  ingresada  es incorrecta. Ingrese una expresiónregular valida.” por la salida estándar de errores y se deberá devolver un 10como resultado (como código de retorno del script). 
Si el script en Python recibe el modificador -o, ordenará la salida por uno de tres posibles criterios. Si se  recibe acomo  parámetro  de  la  opción -o(el  usuario  ingresa  en  la  línea  de  comandos -o a), entonces  se  ordenarán  los  correos  electrónicos  en  forma alfabéticacreciente.  Si  se  recibe dcomo parámetro de la opción -o(el usuario ingresa en la línea de comandos -o d), entonces se listarán los correos ordenados por dominio (dentro del mismo dominio el orden no importará) en orden alfabéticocreciente por el dominio. Si se recibe l(ele) como parámetro de la opción -o(el usuario ingresa en la línea  de  comandos -o l),  entonces  se  listarán  los  correosordenados  porsu  largo  en  caracteres  en forma  creciente  (correos  con  menor  cantidad  de  caracteres  primero  y  los  que  tienen  la  cantidad mayor de caracteres al final).  Si se recibieranmásde una opción de ordenamiento,se considerará una cualquiera de ellas (por ejemplo, la última de ellas, es decir, la que se ingresóúltimo en la línea de comandos al ejecutarse el script Python) y se ignorará lao las demás.
Elscript de Python deberá utilizar apropiadamente el script del ejercicio 1, no resolviendo por símismo  (en  ningún  caso)directamentelabúsqueda  de  los  correos  electrónicos  en  el filesystem.El script en Pythondeberá llamar al script del ejercicio 1 con los parámetros adecuados para  producir  la  salida  a  mostrar  como  resultado(haciendoel  procesamiento  necesario dela informaciónbrindada por el script del ejercicio 1para adaptarla a los pedidos del usuario). Observe el paralelismo  que  hay  entretres  de  los  modificadoresy además  eldirectorio del script  en  Python (modificadores-r,-ty -d dom) y los modificadoresy directoriodel script del ejercicio 1.
El  script  en  Python reutilizarála  verificación  de  errores del  script  del  ejercicio  1  (si se producenerrores al ejecutarse ese script)y reutilizarátambién losmensajes que envíaa su salidaestándar de errores(los mensajes de error, que correspondanal ejercicio 1, deben ser generados por el script del ejercicio  1,  haciendo  el  script  en  Python  un  aprovechamiento  de  los  mismos,  reenvidándolos  a  su propia  salida  estándar  de  errores).  El  código  de  retorno  del  script  en  Python  será tambiénel  que retorne el script del ejercicio 1en estos casos.
En caso que existan errores en la interpretación de los argumentos recibidos(cantidadincorrecta de parámetros, modificadores inválidos,parámetros  incorrectos),  se  retornara  un 20como  código  de retornoy  se  desplegará,  por  la  salida  estándar  de  errores,  una  descripción  resumida  de  la  sintaxis general del comando(del script en Python).
i  no  se  producen  errores  (se  ha  pasado  un  camino  a  undirectorioválido, no  hay  problemas  de acceso a ély no hay modificadores incorrectosni otros errores en el ingreso de los parámetros), se desplegará la información que retorna el script del ejercicio 1 por su salida estándar,procesada y con las características apropiadas según los modificadoresy parámetrosindicadospor el usuario.En este caso, el código de retorno deberá ser 0
Si  no  hay  erroresy  además  no  haycorreos  electrónicos para  listar,  también  se  aprovecharáel mensaje que envía el script del ejercicio 1 en ese caso (por su salida estándar de errores), que será reenviado por la salida estándar de errores del script en Python. Como no es un error que no existan correos electrónicos encontrados(desde el punto de vista de la sintaxis de este script), el código de retorno  del  script  de  Python tambiénserá  cero  en  este  caso(como  se  da tambiéncon  el  script  del ejercicio 1 en este mismo caso).
