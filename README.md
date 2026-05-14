# WordPress Docker

Minimal local WordPress development setup using Docker Compose.

## Project Structure

```text
.
├── docker-compose.yml
├── .env
├── .env.example
├── .gitignore
├── README.md
├── wp-content/
│   ├── mu-plugins/
│   ├── plugins/
│   ├── themes/
│   └── uploads/
├── db/
│   └── backups/
├── nginx/
├── php/
└── scripts/
```

## Services

- `nginx` on `http://localhost:8080`
- `wordpress` running PHP-FPM
- `mysql` for the WordPress database

## How It Works

- Nginx serves the site and forwards PHP requests to WordPress PHP-FPM.
- WordPress core is stored in a Docker named volume.
- Local custom code lives in `wp-content/`.
- MySQL data persists in a Docker named volume.
- `.env.example` is the tracked template for local configuration.

## Setup

```bash
cp .env.example .env
docker compose up -d
```

Open `http://localhost:8080` and complete the WordPress installer.

## Common Development Paths

- Themes: `wp-content/themes/your-theme`
- Plugins: `wp-content/plugins/your-plugin`
- Must-use plugins: `wp-content/mu-plugins`
- Media uploads: `wp-content/uploads`
- Database backups: `db/backups`
- Nginx config: `nginx/default.conf`
- PHP config: `php/custom.ini`

## Stop

```bash
docker compose down
```

## Reset Data

This removes containers and the database volume.

```bash
docker compose down -v
```

## Configuration

Update `.env` to change:

- database name
- database user and password
- MySQL root password
- WordPress port

## Notes

- `wp-content/uploads/` is ignored by git because it is generated content.
- WordPress core is not committed to git; it is created inside the `wordpress_core` Docker volume.
- Default credentials in `.env.example` are for local development only.
