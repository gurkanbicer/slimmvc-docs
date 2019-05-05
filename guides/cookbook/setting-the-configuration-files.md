All of the applications needs fixed and changeable configurations. Keeping changeable configurations on the database isn’t a logical option most times. Therefore, creating configuration files is an option according to applications needs.
 
SlimPHP Extended has two configuration files as default. These files are app/config/slim.php and app/config/database.php. You can create additional configuration files.
 
##### Editing default configuration
 
You can overwrite Slim Framework’s default configurations. SlimPHP Extended is keeping these configurations on the app/config/slim.php file. For example, you can change error indications configuration on this file.
 
##### Editing database configuration
 
You can edit MySQL database configurations on the app/config/database.php file. In addition, you can add multiple MySQL database configurations and you can add other database applications configuration into this file.
 
An example for MySQL database configuration:
 
```php
$configuration['settings']['database']['default'] = [
    'driver' => 'mysql',
    'host' => 'localhost',
    'database' => 'sampleDatabase',
    'username' => 'SampleUser',
    'password' => 'samplePassword!!',
    'charset' => 'utf8',
    'collation' => 'utf8_unicode_ci',
    'prefix' => '',
];
```
 
You can add multiple MySQL database configuration like the below.
 
```php
$configuration['settings']['database']['secondary'] = [
    'driver' => 'mysql',
    'host' => 'localhost',
    'database' => 'sampleDatabase2',
    'username' => 'SampleUser2',
    'password' => 'samplePassword!!',
    'charset' => 'utf8',
    'collation' => 'utf8_unicode_ci',
    'prefix' => '',
];

$configuration['settings']['database']['third'] = [
    'driver' => 'mysql',
    'host' => 'localhost',
    'database' => 'sampleDatabase3',
    'username' => 'SampleUser3',
    'password' => 'samplePassword!!',
    'charset' => 'utf8',
    'collation' => 'utf8_unicode_ci',
    'prefix' => '',
];
```
 
##### Creating new configuration files
 
You can create new configuration files. These configuration files should be on the app/config directory. In addition, the variable that keeping configurations should be named $configuration. When the configuration files are ready to integrate on the project, you should add this configuration file on the app/config/config.php file like the below.
 
```php
require_once DIR_CONFIG . '/sample.php';
```

An example for this configuration file:

```php
$configuration['settings']['sample'] = [
    'option1' => 'value1',
    'option2' => 'value2',
    'option3' => 'value3',
];
```
 
##### Using the configurations
 
You can use configurations on the controllers. But, it isn’t limited to Controllers. You can use configurations on the model files, library files, core files, and dependencies.
 
Firstly, you should add the following code to the top of the file.
 
```php
use SlimFacades\Settings;
```
 
After then, you can get any configuration parameter like the following.
 
```php
$info = Settings::get()['sample'];
```
