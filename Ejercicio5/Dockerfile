# Usa la imagen base de PHP con Apache
FROM php:7.4-apache

# Copia los archivos HTML, CSS, imagen de fondo y PHP al directorio raíz del servicio web
COPY index.html estilo.css docker.png mes.php /var/www/html/

# Exponer el puerto 80 para que el servidor web sea accesible desde el exterior
EXPOSE 80
