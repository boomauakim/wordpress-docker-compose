# WordPress Docker Compose

Ready to use WordPress with Docker and Docker Compose

## Technology Stack
- MariaDB
- NGINX
- PHP
- Let's Encrypt

## Usage
1. Clone repository 
```
git clone https://github.com/boomauakim/wordpress-docker-compose.git
```
2. Make copy of `.env` from `.env.example` and edit the data in file
3. Replace `your_domain` with your domain in all files
4. Repalce `sammy@your_domain` with your email
5. Start container with docker-compose 
```
docker-compose up -d
```
6. Check your certifications from Certbot
```
docker-compose exec webserver ls -la /etc/letsencrypt/live
``` 
It will show the `your_domain` directory in the output. If it doesn't appear, try re-creating the certbot container again
```
docker-compose up --force-recreate --no-deps certbot
```
7. Stop webserver container
```
docker-compose stop webserver
```
8. Comment out line `44`, then uncomment lines `45` and `46` in `docker-compose.yml`. After that, run this command to recreate the web server container
```
docker-compose up -d --force-recreate --no-deps webserver
```
9. Browse your domain
10. Let's install WordPress!

## Renew the Let's Encrypt certificate
1. Add the line below to the crontab
```
$ 0 12 * * * [Repository's absolute path]/scripts/ssl_renew.sh >> /var/log/cron.log 2>&1
```
2. Monitor whether it worked by checking the crontab log message
```
$ tail -f /var/log/cron.log
```

## Volumes
- db: MariaDB data
- wordpress: WordPress files
- certbot-etc: SSL Certificate files

## References
- [How To Install WordPress With Docker Compose](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-docker-compose).
