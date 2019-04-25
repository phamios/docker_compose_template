docker-compose -f ten_file_yml up -d

check / start: 
docker run --rm -h myapp.mydomain.com php:7.0-apache

Truy cập một Container đang chạy trong Docker
1- lấy ID của container : docker ps -a
2-truy cập Container:  docker exec -it <container_id> /bin/bash

check log cuar container: docker logs --details < container id>
