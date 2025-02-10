# Tarea6SXE
Práctica de Docker con PrestaShop. A continuación, se detallan los pasos realizados con los comandos utilizados y una breve descripción de cada uno.

# 1. **Descargar la imagen de PrestaShop**
   - Comandos utilizados:
     ```bash
     docker pull prestashop/prestashop:latest
     docker images
     ```
   - Descripción:
     - Se descarga la imagen de PrestaShop desde Docker Hub.
     - Se verifica que la imagen se haya descargado correctamente con `docker images`.

# 2. **Crear un archivo `docker-compose.yml`**
   - Comandos utilizados:
     ```bash
     nano docker-compose.yml
     ```
   - Descripción:
     - Se crea un archivo `docker-compose.yml` en el directorio del proyecto para definir los servicios de Docker.

# 3. **Agregar configuración al archivo `docker-compose.yml`**
   - Contenido a añadir:
     ```yaml
     version: '3.1'
     services:
       db:
         image: mysql:5.7
         environment:
           MYSQL_ROOT_PASSWORD: my_root_password
           MYSQL_DATABASE: prestashop
           MYSQL_USER: prestashop_user
           MYSQL_PASSWORD: prestashop_password
         volumes:
           - db_data:/var/lib/mysql
       prestashop:
         image: prestashop/prestashop:latest
         environment:
           DB_SERVER: db
           DB_NAME: prestashop
           DB_USER: prestashop_user
           DB_PASSWD: prestashop_password
         ports:
           - "8080:80"
         volumes:
           - prestashop_data:/var/www/html
         depends_on:
           - db
     volumes:
       db_data:
       prestashop_data:
     ```
   - Descripción:
     - Se define la configuración necesaria para crear el contenedor de PrestaShop y la base de datos MySQL.

# 4. **Iniciar los contenedores**
   - Comandos utilizados:
     ```bash
     docker compose up -d
     ```
   - Descripción:
     - Se inician los contenedores de PrestaShop y MySQL en segundo plano.

# 5. **Acceder a la instalación de PrestaShop**
   - Descripción:
     - Para acceder a la instalación de PrestaShop, abre tu navegador y dirígete a `http://localhost:8080`.
    
![Captura desde 2024-11-04 10-50-24](https://github.com/user-attachments/assets/e484d29e-d701-4e5f-9c2c-f947a0ca01a0)  
![Captura de pantalla de 2025-02-10 10-02-13](https://github.com/JavierP5/Tarea6SXE/blob/main/Captura%20de%20pantalla%20de%202025-02-10%2010-02-13.png)  
![Captura 3](https://github.com/JavierP5/Tarea6SXE/blob/main/Captura%20de%20pantalla%20de%202025-02-10%2010-11-31.png)  
![Captura 4](https://github.com/JavierP5/Tarea6SXE/blob/main/Captura%20de%20pantalla%20de%202025-02-10%2010-04-05.png)  
![Captura 5](https://github.com/JavierP5/Tarea6SXE/blob/main/Captura%20de%20pantalla%20de%202025-02-10%2010-04-14.png)  
![Captura 6](https://github.com/JavierP5/Tarea6SXE/blob/main/Captura%20de%20pantalla%20de%202025-02-10%2013-32-36.png)  
![Captura 7](https://github.com/JavierP5/Tarea6SXE/blob/main/Captura%20de%20pantalla%20de%202025-02-10%2013-34-30.png)  

# 6. **Detener los contenedores**
   - Comandos utilizados:
     ```bash
     docker compose down
     ```
   - Descripción:
     - Se detienen y eliminan los contenedores creados por Docker Compose.

# 7. **Verificar el estado de los contenedores**
   - Comandos utilizados:
     ```bash
     docker ps
     docker logs prestashop
     docker logs db
     ```
   - Descripción:
     - Se verifican los contenedores en ejecución y se consultan los registros para asegurarse de que están funcionando correctamente.

---
