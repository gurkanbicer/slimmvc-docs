The installation steps are so simple for **SlimMVC**. You can download the latest version of the repository to your local environment via [this link](https://github.com/gurkanbicer/slimmvc/archive/master.zip) or you can clone the latest version of the repository to your local environment via the following command.

```git
git clone https://github.com/gurkanbicer/slimmvc.git
```

Also, you can fork the repository on the **GitHub** and you can clone your own **GitHub** repository to your local environment.

When you prepare your local environment, the directory tree will be like the below;

```none
- app
  + config
  + controllers
  + core
  + data_cache
  + facades
  + helpers
  + libraries
  + logs
  + middlewares
  + models
  + vendor
  + views
  + views_c
- public
  + assets
  + contents
```

If you’re using Apache web server on your local environment, no need to configuration changes. But, if you’re using Nginx server or another web server software, you should visit [Web servers](https://www.slimmvc.com/docs/get-started/web-servers) page for the configuration samples.

##### The System Requirements

The **Slim Framework** requires PHP 5.5 and newest versions. But, the **SlimMVC** requires PHP 7.1 and newest versions. In addition, it requires the URL rewrite feature on the web server.

The **SlimMVC** becomes with **illuminate/database** package. If you want to use MySQL database on your app, MySQL service and the related MySQL driver for PHP must be installed on your local environment and your web server. We suggest MySQL 5.7+ or MariaDB 10+ versions for MySQL service. 
 
##### No need to the Composer

The **SlimMVC** isn’t a package. It’s a working environment. It becomes with **Slim Framework**’s latest version and a few packages what needs to basic projects. Therefore, you can’t download it via Composer.

But, every project needs to Composer. Maybe, you can want to download a package when you preparing your app, of course, you can use Composer.