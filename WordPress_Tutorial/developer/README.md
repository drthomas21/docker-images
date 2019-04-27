#Build Command
docker build -t wordpress-guide/developer:1.0.1 .

#Container Run Command
docker run -dit \
--name wordpress-dev \
-v /var/www/sites/WordPress_Tutorial:/var/www/sites/WordPress_Tutorial \
-v /var/www/conf:/var/www/conf \
--link mysql-wordpress:mysql-wordpress \
--add-host dev.superwordpressguide.com:127.0.0.1 \
wordpress-guide/developer:1.0.1
