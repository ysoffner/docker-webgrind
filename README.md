[![Build Status](https://travis-ci.org/ysoffner/docker-webgrind.svg?branch=master)](https://travis-ci.org/ysoffner/docker-webgrind)

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
#### Init your compose
`$ docker-compose up -d`

#### Internal Access 
URL: http://localhost:1000
> I use the port `1000` for NGINX

> PHP5.6 `9001`

> PHP7.1 `9002`

> PHP7.2 `9003`

#### Using NGINX to Access your project
Edit the `config/nginx.conf` and uncomment all the seccond `server`, and edit for your project

In docker-compose.yml create port in nginx service

Change the `/some/path/file` of `config/nginx.conf` and set the variable `$PACKAGE` with the same project directory. Example: `PACKAGE=/var/www/test docker-compose up -d` (see in .travis.yml).