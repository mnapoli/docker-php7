# PHP 7 Docker image

This is yet another PHP 7 Docker image except this one contains Composer and Puli. Both are installed as Phars globally (`composer` and `puli` commands).

## Usage

With Docker:

```
docker run mnapoli/php7-cli php -v
```

With Docker Compose:

```yml
app:
    image: mnapoli/php7-cli
    ...
```

Here is an example to mount the local directory and run [PHP's built-in webserver](http://php.net/manual/en/features.commandline.webserver.php) for developing locally:

```yml
# docker-compose.yml
app:
    image: mnapoli/php7-cli
    ports:
        - "8080:8000"
    volumes:
        - .:/app
    working_dir: /app
    command: "php -S 0.0.0.0:8000"
```

Running `docker-compose up` will start the webserver. The application will be accessible at http://localhost:8080.

## Composer and Puli

With Docker:

```
docker run mnapoli/php7-cli composer --version
```

With Docker Compose (and the `docker-compose.yml` example from above):

```
# Composer update
docker-composer run app composer update
# Puli build
docker-composer run app puli build
```
