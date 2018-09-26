# docker-php-mysql-template 
# Readme.txt 
# Author: Ben Sun
# Date: 2018/09/25
# required software: docker, docker-compose

A. Untar docker-php-mysql-template.tgz
   mv docker-php-mysql-template docker-php-mysql-[YOUR_APP]
   cd docker-php-mysql-[YOUR_APP]

B. Change 1 to 2-8 port or port x
In docker-compose.yml
1. Change 81 to 8x (8100 to 8x00, 8180 to 8x80, 8190 to 8x90)
2. Change 91 to 9x (9100 to 9x00)
3. Change 16 to x6 (3316 to 33x6)
In nginx/conf.d/nginx.conf
4. Change 91 to 9x (9100 to 9x00)

C. Choose 7.0-fpm or 5.6-fpm
1. default is 7.0-fpm
2. use the Docker.5.6-fpm and docker-compose.yml.5.6-fpm for 5.6-fpm.
  rm Docker; ln -s Docker.5.6-fpm Docker
  rm docker-compose.yml; ln -s docker-compose.yml.5.6-fpm docker-compose.yml

D. SSL is off at the moment.
1. It is only set up in 01-docker-php-mysql-ypets
  In docker-compose.yml
  1. Uncomment '443:443'
  2. cp -r 01-docker-php-mysql-ypets/nginx/ssl to destination folder
  In nginx/conf.d/nginx.conf
  3. Uncomment the following lines.  Update the correct ssl_certificate and ssl_certificate_key files 

    # Uncomment for https
    #listen 443 default_server ssl;
    ...
    # Uncomment for https
    #ssl_protocols TLSv1.2 TLSv1.1 TLSv1;
    #ssl_certificate /etc/nginx/ssl/certs/[yowpets_com_a282a_bba27_1544159174_ed796edce987fc6f71eaf26fc846e46f.crt];
    #ssl_certificate_key /etc/nginx/ssl/certs/[a282a_bba27_197ca22e9187a8d81abe2394e36f41bb.key];
    ...

E. Start up
1. Use 'docker-compose up'  
  $ docker-compose down;sleep 3; docker-compose up
2. Use a browse and go to localhost:8x00/info.php to see output from phpinfo
3. Use a browse and go to localhost:8x80 => phpmyadmin8x80
  import data 
4. Copy your code to code directory

