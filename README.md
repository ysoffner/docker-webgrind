### Docker Compose to use webgrind in different php versions

##### Install in the same directory
If you want to install in the same directory of this repository, do it:
```
git clone https://github.com/ysoffner/docker-webgrind.git
cd docker-webgrind

bash configs/webgrind.sh
```

#### Edit your docker-compose.yml with your project directory
Edit your config `$ vim docker-compose.yml`, search and replace `- /file/path/to_analyse` with your project directory.

#### Choose your version of PHP into config of nginx
Edit nginx config `$ vim configs/nginx.conf`

Uncomment the version of your preference 
```
    #fastcgi_pass ysoffner-server-php5:9000;
    fastcgi_pass ysoffner-server-php7:9000;
```
