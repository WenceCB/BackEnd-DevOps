#INSTALACIÓN NODE Y NPM

	sudo apt-get install node-legacy npm
	
#GENERAR ARCHIVOS LOCALES CARACTERES ISO

	sudo dpkg-reconfigure locales
	
# CREACIÓN USUARIO NODE

	sudo adduser node

# CREACIÓN DIRECTORIO WWW

	En la ruta /var
	sudo mkdir www
	
# CAMBIAR PERMISOS CARPETA

	sudo chown -R node:node <nombre_carpeta>
	
# INSTALACIÓN DE NGINX Y PM2

	sudo apt-get install nginx
	sudo npm install pm2 -g
	
	pm2 start "archivo.js" --name “Nombre"
	
# CONFIGURACIÓN AZURE

	Edición de puertos 80 > 80
	Edición de puertos 3000 > 3000
	
# EDITAR CONFIRUACIÓN NGINX

	Editar /etc/nginx/sites-enables/default
	>> Indicar ruta con index.html por defecto
	
	Crear un nuevo archivo de configuración con cabecera propia
	para servir archivos estáticos
	
	erver {
        listen 80;
        listen [::]:80;

        root /var/www/node-web;
        index index.html index.htm;

        server_name wencedev.cloudapp.net; # dominio

	location ~ ^/(css/|img/|js/|sounds/|images/|jpg) {
	add_header X-Author "@WenceCB";
  	root /var/www/nodepop/gitNodePractica/nodepop/nodepop/public;
  	access_log off;
  	expires max;
	}

	 location / {
                proxy_pass http://127.0.0.1:3000/;
                proxy_redirect off;
        }
}

# DIRECCIÓN SERVIDOR CON NODEPOP

[http://wencedev.cloudapp.net](http://wencedev.cloudapp.net)

# DIRECCIÓN CON ARCHIVOS ESTÁTICOS

[http://wencedev.cloudapp.net/images/bici.jpg](http://wencedev.cloudapp.net/images/bici.jpg)

[http://wencedev.cloudapp.net/stylesheets/style.css](http://wencedev.cloudapp.net/stylesheets/style.css)

# DIRECCIÓN IP REDIRIGIDO A STICKY-FOOTER

[http://104.214.30.227/](http://104.214.30.227/)
