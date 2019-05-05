Publishing the project is an important matter like preparing the project. When you’re ready to publish your project, maybe you can want to remove unused packages, core files and facade files from your project. In addition, you can want to hide PHP warnings and errors.

If you will remove unused packages, core files, and facade files from your project, you shouldn’t hide PHP warnings and errors in the first step. Because somethings can go wrong.

##### Removing unused packages

Before the start, you should be careful. Open the app/composer.json file and check the packages. If you decide which package will remove, you should edit and run the following command.

```none
php composer remove anOwner/samplePackage
```

Some of the packages may be predefined to the Dependency Container. Open the app/core/dependencies.php file and check that package in this file. An example;

```php
$container['samplePackage'] = function() {
    $samplePackageRef = new samplePackage();
    return $samplePackageRef;
};    
```

##### Removing unused facade files

Before the start, you should be careful. Some of the facades may be used on the core files even you don't use on any controller, model, and library file.

Firstly, open the app/core/facades.php file and remove the related code in this file. After then, you can delete this facade from the app/facades directory.

The facades can be defined in the app/core/facades.php file like the following:

```php
require_once DIR_FACADE . '/sampleFacade.php';
```

##### Removing unused core files

Before the start, you should be careful. Some of the core files may be predefined in the app/core/autoload.php or app/core/dependencies.php files. 

If you decide which core file will be removed, you should check both of files. The core files can be defined in the app/core/autoload.php file like the following.

```php
require_once DIR_CORE . '/database.php';
```

The core file can be defined in the app/core/dependencies.php file like the following.

```php
$container['database'] = function($container) {
    $database = new Database($container);
    return $database;
};
```

Firstly, you should remove these codes from both of files. After then, you can delete this core file from the app/core directory.

##### Hiding PHP warnings and errors

Open the app/config/slim.php file and find the following code.


```php
$configuration['settings'] = [
    ...
    'displayErrorDetails' => true,
    ...
];
```

Change it like the following.

```php
$configuration['settings'] = [
    ...
    'displayErrorDetails' => false,
    ...
];
```

##### You’re ready 

You’re ready to publish. You can use an FTP/SFTP client for uploading your project files to the web server or you can use Git commands for clone the project to your web server, if you have Git project.
