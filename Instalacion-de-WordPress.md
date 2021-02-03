# Instalación de WordPress en nuestra VPS

Primero de todo, aquí explicaremos como instalar y hacer funcionar de forma correcta WordPress en nuestra VPS. ¿Y qué es WordPress? Un sistema de gestión de contenido que, aunque hay muchos más, es de los más conocidos en el mercado. Esta vez lo haremos en nuestra VPS para mayor comodidad, pudiendo tener localizada en esta nuestra página web.

El primer paso que debemos realizar es acceder como root a nuestro mysql anteriormente instalado en nuestra vps con el comando "mysql -u root -p". Para nuestro caso, crearemos una base de datos específica para WordPress, para evitar que haya conflictos con otras bases de datos que queramos almacenar por separado.

![](./imagenes/img-1.png)

También crearemos un usuario por separado que tendrá todos los privilegios y será el que gestionará nuestra base de datos específica de WordPress, de ahí su nombre WordPressUser.

![](./imagenes/img-2.png)

Una vez hecho esto, salimos de mysql por el momento. Lo siguiente que procedemos a hacer es crear un archivo de configuración al que llamaremos WordPress.conf, que será una réplica del archivo de configuración que ya tenemos por defecto.

![](./imagenes/img-3.png)

![](./imagenes/img-4.png)

Además de esto, crearemos un nuevo directorio específico para WordPress en /var/www/ que se llamará wordpress

![](./imagenes/img-5.png)

El archivo WordPress.conf será el archivo de configuración de apache para la prueba que vamos a hacer. En el archivo, podemos habilitar .htaccess de la siguiente forma:

![](./imagenes/img-6.png)

A continuación, podemos habilitar el mod_rewrite para usar la función de enlace permanente de WordPress:

![](./imagenes/img-7.png)

Tras hacer todo esto, puedes reiniciar el servidor con el comando que siempre utilizas, "sudo systemctl restart apache2". Con todo esto, hemos preparado nuestra vps para la instalación de WordPress y ahora procederemos a hacer la propia instalación y configuración de este.

Comenzamos la instalación con el siguiente paquete:

![](./imagenes/img-8.png)

![](./imagenes/img-9.png)

Aquí mismo podemos crear un archivo .htaccess:

![](./imagenes/img-10.png)

Lo siguiente que debes hacer es cambiar el nombre del archivo wp-config-sample.php con el comando:

![](./imagenes/img-11.png)

Y lo siguiente para hacer es crear la siguiente carpeta en esta dirección:

![](./imagenes/img-12.png)

Hasta aquí tendremos lista la configuración inicial, la cual podemos copiar en el documento raíz para más comodidas.

![](./imagenes/img-13.png)

Para asegurarte de que todo funcione correctamente, debes pasar la propiedad de los archivos de WordPress a los usuarios y grupos de www-data. Para cambiar la propiedad, puedes usar este comando:

![](./imagenes/img-14.png)

Además de esto, debemos establecer el permiso correcto para los directorios y archivos de la siguiente forma:

![](./imagenes/img-15.png)

A continuación tendremos que generar las claves salt de WordPress:

![](./imagenes/img-16.png)

Si lo ejecutas varias veces obtendrás un resultado diferente cada vez y verás una lista de claves salt diferentes. El resultado del comando anterior debe copiarse y agregarse al archivo wp-config.php:

![](./imagenes/img-17.png)

Este archivo también contiene una configuración básica de base de datos en la parte superior. Reemplazamos DB_NAME, DB_USER, DB_PASSWORD con los valores que hemos creado anteriormente para WordPress.

![](./imagenes/img-18.png)

Procedemos a guardar el archivo con dichas configuraciones y con todo esto hemos terminado con las configuraciones que se hacen en el backend, así que ahora procedemos a las configuraciones en la interfaz gráfica, terminando de esta forma nuestra instalación de WordPress.

![](./imagenes/img-19.png)

![](./imagenes/img-20.png)

![](./imagenes/img-21.png)

![](./imagenes/img-22.png)


