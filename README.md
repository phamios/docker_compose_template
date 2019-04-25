version: "3"

services:
  nginx-proxy:
    image: jwilder/nginx-proxy
    volumes:
      - /var/run/docker.sock:/tmp/docker.sock:ro

  mariadb:
    image: mariadb
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: 1q2w3e4r
    ports:
      - 13306:3306
    volumes:
      - D:/Docker/mariadb/:/var/lib/mysql
  
  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    restart: always
    environment:
      PMA_HOST: mariadb
      PMA_USER: root
      PMA_PASSWORD: 1q2w3e4r
    ports:
      - 10080:80
  
  thietbidien:
    image: php:5.6-apache
    restart: always
    environment:
      VIRTUAL_HOST: thietbidien.test
      VIRTUAL_PORT: 80
      MYSQL_HOST: mariadb
      MYSQL_USER: root
      MYSQL_PASS: 1q2w3e4r
    volumes:
      - D:/Docker/thietbidien:/var/www/html
  
  localhost:
    image: php:7.2-apache
    restart: always
    environment:
      VIRTUAL_HOST: localhost.test
      VIRTUAL_PORT: 80
      MYSQL_HOST: mariadb
      MYSQL_USER: root
      MYSQL_PASS: 1q2w3e4r
    volumes:
      - D:/Docker/localhost:/var/www/html

# them 127.0.0.1 thietbidien.test vao file hosts
