# Setting up PHP
To setup PHP we need to few PHP environment variables in **php.ini** file

The **php.ini** file can be located depending on your PHP installation.

Common directory location to find the **php.ini** file is

```
/etc/php/{php-version}/cli/php.ini
```

* max_input_time = 3600
* post_max_size = 1024 (if a file larger than 1GB is need to be uploaded then it my have to be changed depending on the requirement)
* file_uploads = On (By default it will be turned On, but if not then turn it On)
* upload_max_filesize = 1024M (it can also be modified depending on the requirment)

## Setting up PHP extentions

* **MCrypt:** Your server must have PHP MCrypt extention enabled. To enable it in PHP 7.0, you can go to cPanel and Enable it from Select PHP Version. option. However MCrypt was deprycated in PHP Version. 7.2. So to install MCrypt in PHP 7.2 you will need these following CLI commands
    * sudo apt-get -y install gcc make autoconf libc-dev pkg-config
    * sudo apt-get -y install libmcrypt-dev
    * sudo pecl7.2-sp install --nodeps mcrypt-snapshot
    * For more reference visit this link: https://serverpilot.io/docs/how-to-install-the-php-mcrypt-extension

* **Bcmath:** You can install it from Cpanel as well but if you want to install it from CLI then the command is 
sudo apt install php{php-version}-bcmath

# Setting Up API Gateway

### Installing

Connect via SSH

Go to "public_html"

```cd \public_html```

Create a directory named "butu_api_gateway" in the root directory

```mkdir butu_api_gateway```

Go to the directory "butu_api_gateway"

```cd butu_api_gateway```

Initialize Git

``` git init ```

Add git remote origin

```git add remote origin {git-remote-origin}```

Pull project from remote repository

```git pull origin master```

Install dependencies with composer

```composer install```

Additional set-up

Inside the "config" folder, there is a file called "ServiceUrls.php". It has all the service URLs and every API Gateway APIs are extending Service URLs from this file. Please change it according to your need.

```
<?php
namespace app\config;

class ServiceUrls
{
    const UPLOAD_SERVICE = 'http://localhost:8080';
    const MOVIE_SERVICE = 'http://localhost/butu_movies';
}
```

### All set!

