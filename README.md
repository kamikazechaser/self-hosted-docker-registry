#### Self Hosted Docker Registry

*Configuration*:

- Replace $DOMAIN and $EMAIL values from the files with your values
- Point the domains below to your server IP
- Add your Bcrypt hashed password (`htpasswd -nB username`) to `configs/registry-auth` users section
- Add the plain password created above (while on the server) to `configs/registry-ui-config`
- Create certs with `openssl req  -nodes -new -x509  -keyout cert.key -out cert.pem` inside `configs/certs`
- Run `docker-compose up -d`

Endpoints:

- docker.$DOMAIN (Registry)
- registry.$DOMAIN (Registry UI)
- traefik.$DOMAIN (Traefik Dashboard)

Docs reference:

- Official Docker Registry - https://docs.docker.com/registry/
- Docker Registry Auth - https://github.com/cesanta/docker_auth
- Docker Registry UI - https://github.com/Quiq/docker-registry-ui

Notes:

- Registry UI logs are temporary (container lifetime)
- s3 compatible storage needs move and rename s3 API compatibility (Amazon s3 supports this, most self-hosted s3 don't)

Usage:

- Login with `docker login docker.$DOMAIN`
- Tag your personal images with `docker.$DOMAIN/NAMESPACE/IMAGE_NAME:TAG`
