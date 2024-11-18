# Práctica 01: SQLi
## Preparativos
1. Kali Linx (como máquina virtual o huésped)
2. Máquina OWASP que hostea la web vulnerable
3. Acceso al navegador para interactuar con la aplicación v`unerable y comprobar los resultados.

## Comprobación de la vulnerabilidad del sitio
1. Iniciamos la máquina virtual OWASP y la máquina Kali. Anotaremos la IP que nos proporciona la máquina OWASP.
![1731518315759](image/instrucciones/1731518315759.png)
En mi caso, la IP es la `192.168.122.4`. Accedemos a la página poniendo dicha IP en el navegador.
![1731518439008](image/instrucciones/1731518439008.png)
2. Seleccionamos el "bug" que querramos trabajar, en este caso `SQL Injection (Search/GET)` y le damos a `Hack`.
<br>
![1731518529692](image/instrucciones/1731518529692.png)

3. Nos aparecerá un buscador de películas. Introducimos una comilla `'` en la barra de busqueda para comprobar la vulnerabilidad del sitio a inyecciones `SQL`.
![1731518610325](image/instrucciones/1731518610325.png)
4. Podemos observar que la página no maneja correctamente los errores de `SQL`, tanto es así que nos muestra que la página usa `MySQL`.
5. También observamos que la URL cambia según lo que introduzcamos en el buscador, en este caso la palabra `spider`. De esta forma también vemos que la página usa `PHP`.
![1731518776946](image/instrucciones/1731518776946.png)
![1731518800391](image/instrucciones/1731518800391.png)

<div style="page-break-after: always;"></div>

## Obtención de usuarios y contraseñas
### bWAPP
1. Le daremos a la tecla `F12`, abriendo las opciones de desarrollador y nos iremos al apartado de `Application`. Ahí, nos iremos a la parte de `Cookies`, seleccionaremos la página de `bWAPP` (sabremos cuál es por la IP) y buscaremos la cookie llamada `PHPSESSID`. Copiaremos su valor. 
![1731518948705](image/instrucciones/1731518948705.png)
2. Abriremos una terminal en Kali Linux y escribiremos el siguiente comando, cambiando la dirección y el valor del `PHPSESSID` por los que sean procedentes en su caso. 
![1731928498929](image/instrucciones/1731928498929.png)
Y nos mostrará las bases de datos disponibles.
![1731928556189](image/instrucciones/1731928556189.png)
3. Ejecutamos el siguiente comando para mostrar las tablas de la base de datos `bWAPP`.
![1731928646757](image/instrucciones/1731928646757.png)
Nos saldrán algunas opciones y le daremos a todas que sí o a la tecla `Enter` y, tras una pequeña espera, nos aparecerán las tablas de `bWAPP`.
![1731928787372](image/instrucciones/1731928787372.png)
4. Usaremos el siguiente comando para mostrar el contenido de la tabla `users`.
![1731928886207](image/instrucciones/1731928886207.png)
![1731929056775](image/instrucciones/1731929056775.png)
5. Ejecutamos el siguiente comando para mostrar la información de todos los usuarios de la tabla, seleccionando previamente los campos a mostrar.
![1731929227846](image/instrucciones/1731929227846.png)
Daremos a todo que sí o a `Enter`y tras esperar un poco nos aparecerán los usuarios.
![1731929318088](image/instrucciones/1731929318088.png)
Esta información será guardada en un fichero llamado `users.csv` en la ruta que aparece en la imagen para poder consultarlo en otro momento.

### WordPress
Para repetir este proceso pero con la base de datos de `WordPress`, bastará con:
1. Comprobar su existencia con el siguiente comando
![1731928498929](image/instrucciones/1731928498929.png)
![1731929610099](image/instrucciones/1731929610099.png)
2. Mostrar las tablas de la base de datos.
![1731929751915](image/instrucciones/1731929751915.png)
![1731929770551](image/instrucciones/1731929770551.png)
3. Mostrar las columnas de la tabla `wp_users`.
![1731929826315](image/instrucciones/1731929826315.png)
![1731929849687](image/instrucciones/1731929849687.png)
4. Mostrar los datos de la tabla seleccionando previamente los campos a mostrar.
![1731929965970](image/instrucciones/1731929965970.png)
Y tras dar a todo que sí o a `Enter`, nos aparecerá la información.
![1731930204829](image/instrucciones/1731930204829.png)