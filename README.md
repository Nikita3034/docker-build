### Includes:
- `nginx 1.19`
- `mysql 5.7`
- `php-fpm 7.4`
- `xdebug 2.9.1`
- `node 16.13.2`
- `npm 7.24.2`
- `composer:latest`

### Environment variables:
- `PROJECTS_PATH` full path to your project
- `PROJECT_NAME` name of your project
- `MYSQL_*` variables for setting MySQL

### Additionally:
- `rebuild.sh` docker rebuild script

### Project development:
- Installing `docker` and `docker-compose` from official sources
- `cp .env.example .env`
- Setting the full path to the project in `.env`
- `docker-compose up -d`
