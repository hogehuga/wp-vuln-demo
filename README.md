# wp-vuln-demo
WordPress vulnerability demo by WordPress4.5.1 and old-plugins.

# how2use
- install docker , docker-compose
- write `stack.yml` docker-compose file.
  - modified from https://hub.docker.com/_/wordpress?tab=description
  - without volumes section
- start container
  - `docker-compose -f stack.yml up`
- and embed the vulnerability.

stack.yml
```
version: '3.1'

services:
  wordpress:
    image: wordpress:4.5.1
    restart: always
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: exampleuser
      WORDPRESS_DB_PASSWORD: examplepass
      WORDPRESS_DB_NAME: exampledb

  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_DATABASE: exampledb
      MYSQL_USER: exampleuser
      MYSQL_PASSWORD: examplepass
      MYSQL_RANDOM_ROOT_PASSWORD: '1'
```

vulnerability enbed image is ...
- https://cloud.docker.com/u/hogehuga/
  - vuln-wp-db
  - vuln-wp451

NEXT step is modify stack.yml to use vulnerability enbed image.
