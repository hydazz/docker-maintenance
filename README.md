## docker-maintenance
Barebones NGINX server, specifically made to be a maintenance page for when your SWAG container is down. Theoretically, when you stop your SWAG container, and spin this one up it should just work. You may need to migrate your SWAG NGINX configs to this container and change file paths, such as ssl certs, etc. and setup a 302 redirect to redirect to maintenace.yourdomain.com.
