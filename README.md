"# FinkenRoulette" 

## Docker

This project can be built as a Docker image. The container serves the built Vite app with Nginx.

CSV files are stored in the `public` directory. Vite copies these files into the production build, so they are baked into the Docker image.

### Docker Compose example

```yaml
services:
  finkenroulette:
    image: ghcr.io/dflvunoooooo/finkenroulette:latest
    container_name: finkenroulette
    restart: unless-stopped

    ports:
      - "8080:8080"

    networks:
      - finkenroulette

    read_only: true
    tmpfs:
      - /tmp
      - /var/cache/nginx
      - /var/run

    security_opt:
      - no-new-privileges:true

    cap_drop:
      - ALL

networks:
  finkenroulette
```