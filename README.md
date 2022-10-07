Symfony Demo Application
========================

The "Symfony Demo Application" is a reference application created to show how
to develop applications following the [Symfony Best Practices][1].

You can also learn about these practices in [the official Symfony Book][5].

Requirements
------------

  * PHP 8.1.0 or higher;
  * PDO-SQLite PHP extension enabled;
  * and the [usual Symfony application requirements][2].

Installation
------------

[Download Symfony][4] to install the `symfony` binary on your computer and run
this command:

```bash
$ symfony new --demo symfdemo
```

Alternatively, you can use Composer:

```bash
$ composer create-project symfony/symfony-demo symfdemo
```

If you want to test the demo without installing anything locally, you can also
deploy it on Platform.sh, the official Symfony PaaS:

<p align="center">
<a href="https://console.platform.sh/projects/create-project?template=https://raw.githubusercontent.com/symfonycorp/platformsh-symfony-template-metadata/main/template-metadata-demo.yaml&utm_content=symfonycorp&utm_source=github&utm_medium=button&utm_campaign=deploy_on_platform"><img src="https://platform.sh/images/deploy/lg-blue.svg" alt="Deploy on Platform.sh" width="180px" /></a>
</p>

Usage
-----

There's no need to configure anything to run the application. If you have
[installed Symfony][4] binary, run this command:

```bash
$ cd symfdemo/
$ symfony serve
```

Then access the application in your browser at the given URL (<https://localhost:8000> by default).

If you don't have the Symfony binary installed, run `php -S localhost:8000 -t public/`
to use the built-in PHP web server or [configure a web server][3] like Nginx or
Apache to run the application.

Usage with xampp windows 
-------------------------
Alternatively you can configure your application to run on Apache (for exemple : xampp windows) :

Enable listening on port 8080 : httpd.conf
```bash
Listen 8080
```

Configure the virtual host : httpd-vhosts.conf
```bash
<VirtualHost *:8080>
    DocumentRoot C:\xampp\htdocs\symfdemo\public
    DirectoryIndex /index.php
    <Directory C:\xampp\htdocs\symfdemo\public>
        AllowOverride None
        Order Allow,Deny
        Allow from All
        FallbackResource /index.php
    </Directory>
    ErrorLog C:\xampp\htdocs\symfdemo\project_error.log
    CustomLog C:\xampp\htdocs\symfdemo\project_access.log combined
</VirtualHost>
```
Then access the application in your browser at the given URL (<https://localhost:8000> by default).


Usaging MySql instead of SqlLite 
--------------------------------
To get your application running with MySql, you have to make some config:

Change .env file to point to MySql database
```bash
#DATABASE_URL=sqlite:///%kernel.project_dir%/data/database.sqlite
DATABASE_URL="mysql://root:@127.0.0.1:3306/symfdemo?serverVersion=mariadb-10.4.11"
```

Create tables on the database whith migration process
```bash
php .\bin\console make:migration
php .\bin\console doctrine:migration:migrate
```
Then access the application in your browser at the given URL (<https://localhost:8000> by default).
