#Build Command
docker build -t signz/developer:1.0.0 .

#Container Run Command
docker run -dit \
--name signz-dev \
-v /var/www/sites/Signz_Remaster:/var/www/sites/Signz_Remaster \
--link mysql-signz:mysql-signz \
--add-host dev.officialsignz.com:127.0.0.1 \
signz/developer:1.0.0
