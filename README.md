# WordPress Docker

Local WordPress with Docker Compose.

## Setup

```bash
cp .env.example .env
docker compose up -d
```

Open `http://localhost:8080`.

## Paths

- Theme: `wp-content/themes/project-theme`
- Plugin: `wp-content/plugins/project-plugin`
- MU plugin: `wp-content/mu-plugins/project-mu-plugins`
- Uploads: `wp-content/uploads`
- Nginx: `nginx/default.conf`
- PHP: `php/custom.ini`

Rename the placeholder folders to your real slugs and update `.gitignore` if needed.

## Commands

```bash
docker compose up -d
docker compose down
docker compose down -v
```

## Recreate

```bash
docker compose up -d --force-recreate wordpress nginx
docker compose up -d --force-recreate db
docker compose up -d --force-recreate
```

## Env

- `WORDPRESS_PORT`
- `WORDPRESS_PHP_VERSION`
- `MYSQL_PORT`
- `MYSQL_DATABASE`
- `MYSQL_USER`
- `MYSQL_PASSWORD`
- `MYSQL_ROOT_PASSWORD`

## DB

- Host: `127.0.0.1`
- Port: `MYSQL_PORT`
- Database: `MYSQL_DATABASE`
- Username: `MYSQL_USER`
- Password: `MYSQL_PASSWORD`

## Debugging

```bash
docker compose ps
docker compose logs -f wordpress nginx db
docker compose exec wordpress sh
docker compose exec db mysql -u"$MYSQL_USER" -p"$MYSQL_PASSWORD" "$MYSQL_DATABASE"
```
