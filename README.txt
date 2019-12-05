
Carpeta cliente : Codigo a introducir en el servidor que proporciona los recursos de la aplicación cliente
Carpeta servidor : Contiene el .jar que ejecuta la parte servidor de la aplicación
Código : Contiene el código del frontend y del backend


A.1 Instalación del software
En este apartado se detalla el proceso de instalación y ejecución del software desarrollado.
Para la ejecución de la aplicación es necesario tener instalado en primer lugar:
• Un sistema gestor de Base de Datos MySql 8.0 o superior
• Un servidor Apache
A continuación se crea la Base de Datos necesaria para la ejecución de la aplicación. Para
ello se realizan los siguientes pasos:
• Ejecutar en un terminal : mysqladmin-uroot–password e introducir la contraseña
del usuario root si se ha especificado durante la instalación de Mysql
• Ejecutar create AdoptApp
• Ejecutar create user ”adoptappadmin@localhost” identified by ’adoptappadmin’
• Ejecutar grant all privileges on adoptapp to adoptappadmin@localhost with
grantoption

Por ultimo ejecutar el script SQL que se adjunta para poblar la base de datos

Para el despliegue del Backend :
• Abrimos una terminal en la ruta del archivo AdoptApp-0.0.1-SNAPSHOT
• Ejecutamos el comando : $java -jar AdoptApp-0.0.1-SNAPSHOT

Para desplegar el Frontend añadimos todos los archivos que lo conforman ( contenidos en la carpeta cliente ) al directorio
htdocs de la carpeta de Apache. Además incluimos en dicha carpeta un fichero .htaccess con
el siguiente contenido:
Options -MultiViews
RewriteEngine On
RewriteCond %REQUEST_FILENAME !-f
RewriteRule ^index.html [QSA,L]
Posteriormente accedemos al fichero \conf\httpd del directorio de Apache y añadimos lo
siguiente:
<Directory />
AllowOverride none
</Directory>
Por último publicamos los recursos del Frontend con el comando httpd desde la carpeta
\bin del directorio de Apache

