# WordPress Docker Compose

Ready to use WordPress with docker and docker-compose

## Technology Stack
- MariaDB
- NGINX
- PHP
- Let's Encrypt

## Usage
1. Run `git clone https://github.com/boomauakim/wordpress-docker-compose.git`
2. Make copy of `.env` from `.env.example` and edit data in file
3. Change 'example.com' to your domain in `nginx/nginx.conf`
4. Run `docker-compose up -d`
5. Access to NGINX Container with command `docker-compose exec nginx bash`
6. Run `openssl dhparam -out /etc/nginx/dhparam.pem 2048` for generate dhparam
7. Uncomment line 37, 51, 52, 58, 59 and 60 in `nginx/nginx.conf`
8. Restart NGINX Container with command `docker-compose nginx restart`
9. Browse your domain
10. Let's build WordPress !

## Usage (Local)
1. Run `git clone https://github.com/boomauakim/wordpress-docker-compose.git`
2. Make copy of `.env` from `.env.example` and edit data in file
3. Run `docker-compose -f docker-compose.local.yml up -d`
4. Browse to `127.0.0.1`
5. Let's build WordPress !

## Volumes
- database: MariaDB data
- logs: NGINX logs
- wordpress: WordPress files
- cert: SSL Certificate files
