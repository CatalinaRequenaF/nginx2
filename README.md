# nginx2

Vamos a https://docs.docker.com/desktop/windows/install/ y procedemos a instalar docker.  
![image](https://user-images.githubusercontent.com/91744454/168906903-664834dd-ba63-4277-ad73-a4a29938d943.png)  

Ejecutamos el .exe descargado.  

![image](https://user-images.githubusercontent.com/91744454/168906956-ba27713a-220a-4f0b-b6c6-92ed285f5298.png)
  
Una vez instalado y al intentar abrirlo nos aparece este mensaje de advertencia:  

![image](https://user-images.githubusercontent.com/91744454/168907045-2d4d9485-055b-4e68-b81f-1019cc9f67c7.png)  

Esto se debe a que no tenemos instalado el WSL2 (Windows Subsystem for Linux) para poder usar Docker desde Windows.  
Lo que haremos será introducir `wsl --install`desde el Powershell y después reiniciar el ordenador.  

![image](https://user-images.githubusercontent.com/91744454/168907445-95536c18-fc89-4aff-9dbb-7db62752acc7.png)  

Una vez se ha reiniciado, intentamos abrir Docker Desktop y se abrirá con normalidad.  

![image](https://user-images.githubusercontent.com/91744454/168907540-0c71bb1d-1faa-4b3b-9402-c1f1381c65f8.png)  
 
Podemos insertar este código para comprobar que funciona correctamente:  

![image](https://user-images.githubusercontent.com/91744454/168907566-bd026ae3-fe72-4744-8cbf-a2a7b4321975.png)  

Ahora introducimos en nuestro PowerShell `docker run --rm -d -p 8080:80 --name Catalina nginx`, creando así el servidor en el puerto 8080,  
instalando la imagen de nginx.

![image](https://user-images.githubusercontent.com/91744454/168907939-a46b92c5-4fbc-4218-92e5-d44c5a24967a.png)  

Así, si accedemos a través del navegador a localhost:8080, podemos ver nginx funcionando:  

![image](https://user-images.githubusercontent.com/91744454/168908602-4c1ce842-7328-4af6-82a3-71df31ea2748.png)  

Ahora paramos la máquina con los comandos `docker stop Catalina`  

Vamos hasta nuestra carpeta de Documentos y creamos una carpeta llamada `Nginx`.   

![image](https://user-images.githubusercontent.com/91744454/168908775-af92edab-f063-4b8c-aec5-91f6f9b7a929.png)  

Dentro de esta misma, creamos otro repositorio llamado `site-content`

![image](https://user-images.githubusercontent.com/91744454/168909146-de73464a-0878-48cc-97fd-6fcdebb349fa.png)  

Dentro de este directorio, creamos un archivo llamado `index.html`, con este contenido:  
![image](https://user-images.githubusercontent.com/91744454/168909322-c363bcfb-6b37-41d1-ad63-94bad8b22ac5.png)
![image](https://user-images.githubusercontent.com/91744454/168909279-27226163-4c66-49bb-92f4-f8560fca03a0.png)  

Ahora ejecutamos esta línea:  
`docker run --rm -d -p 8080:80 --name Catalina -v C:\Users\catal\Documents\Nginx\site-content:/usr/share/nginx/html nginx`  
Este código le dice a nginx dónde se encuentra el HTML.

![image](https://user-images.githubusercontent.com/91744454/168909450-3d8d059c-fd29-45fe-98e1-8ea0c94e9d50.png)  

Podemos observar cómo en el puerto 8080 vemos el contenido de ese HTML:  

![image](https://user-images.githubusercontent.com/91744454/168909510-2a2c989c-c1b8-4cdc-a13d-63c64037d625.png)







