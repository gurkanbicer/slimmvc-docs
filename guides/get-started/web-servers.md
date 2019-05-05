The **SlimMVC** supports all of the popular web server softwares. There is no difference between **Slim Framework** and **SlimMVC**. Therefore, we took reference to the original **Slim Framework** [document](http://www.slimframework.com/docs/v3/start/web-servers.html) when we preparing this document. 

##### Apache configuration

When you install **SlimMVC** or you clone **SlimMVC** on your local environment, the .htaccess file becomes with it. Therefore, no needs any changes. But, maybe, you lost the .htacess file or it becomes needed for some reason, you can use the following configuration in your .htaccess file. There is one rule, the .htaccess file must be in the same directory with the index.php file.

```apache
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_URI} !\.(txt|css|js|jpg|jpeg|png|gif|ico)$
RewriteRule ^ index.php [QSA,L]
```

##### Nginx configuration

If you will use the Nginx server on your local environment or on the web server, you can inspect the following vhost configuration sample. It assumes to the domain name is example.com and the listening port is 80. And, also it assumes your server has PHP-FPM service running on 9000 port. Some of the directives like the server_name, error_log, access_log, and root directive are depended on your environment configuration.

```nginx
server {
    listen 80;
    server_name example.com;
    index index.php;
    error_log /path/to/example.error.log;
    access_log /path/to/example.access.log;
    root /path/to/public;

    location / {
        try_files $uri /index.php$is_args$args;
    }

    location ~ \.php {
        try_files $uri =404;
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        fastcgi_param SCRIPT_NAME $fastcgi_script_name;
        fastcgi_index index.php;
        fastcgi_pass 127.0.0.1:9000;
    }
}
```

##### IIS configuration

If you will use the IIS server, you can use the following configuration into your web.config file.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <rule name="slim" patternSyntax="Wildcard">
                    <match url="*" />
                    <conditions>
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
                    </conditions>
                    <action type="Rewrite" url="index.php" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
```