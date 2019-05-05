The controller files and the functions under these controller loads automatically. Therefore, route defining is enough. But, the layers and the structures using on the Controller can be load with a loader.
 
##### Creating a controller
 
All of the controller files should be on the app/controllers directory. The controller file should be named like **xxxController** for project entirety. The file name and the class name inside this file should be same.
 
There is an example for the controller file to reach all of the layers and structures.
 
```php
<?php
use Psr\Http\Message\ServerRequestInterface as Request;
use Psr\Http\Message\ResponseInterface as Response;
use SlimFacades\Container;
use SlimFacades\Model;
use SlimFacades\View;
use SlimFacades\Helper;
use SlimFacades\Library;
use SlimFacades\Settings;

    Class sampleController {

        private $c;

        public function __construct($container) {
            $this->c = $container;
        }

        public function sample(Request $request, Response $response, $args) {
            // bla bla bla
        }

    }

/* path: ~app/controllers/sampleController.php */
```
 
##### An example of a controller
 
The view layer has been used in the following example. 
 
```php
<?php
use Psr\Http\Message\ServerRequestInterface as Request;
use Psr\Http\Message\ResponseInterface as Response;
use SlimFacades\Container;
use SlimFacades\Model;
use SlimFacades\View;
use SlimFacades\Helper;
use SlimFacades\Library;
use SlimFacades\Settings;

    Class sampleController {

        private $c;

        public function __construct($container) {
            $this->c = $container;
        }

        public function index(Request $request, Response $response, $args) {
            return View::render($response, "index.tpl", []);
        }

    }

/* path: ~app/controllers/sampleController.php */
```
 
There is a route for this controller in the following example.
 
```php
Route::get('/sample', '\sampleController:index');
```
 
##### Using models on the controller
 
Firstly, the model should be defined in the __construct() function of the controller. You can inspect the following example.

```php
public function __construct($container) {
    $this->c = $container;
    Model::load('sample');
}
```
 
Any function in the model file can be called like the following example.
 
```php
$results = Container::get('sampleModel')->getAnyData();
```
 
##### Using library on the controller
 
Firstly, the library should be defined in the __construct() function of the controller. You can inspect the following example.
 
```php
public function __construct($container) {
    $this->c = $container;
    Library::load('sample');
}
```

Any function in the library file can be called like the following example.
 
```php
$results = Container::get('sampleLibrary')->getAnyData();
```
 
##### Using helper on the controller
 
Firstly, the helper should be defined in the __construct() function of the controller. You can inspect the following example.
 
```php
public function __construct($container) {
    $this->c = $container;
    Helper::load('sample');
}
```
 
Any function in the helper file can be called like the following example.
 
```php
$text = pTagFormatter($text, 'text-muted mx-3');
```
 
##### Using view on the controller
 
The view layer is loading automatically in the beginning. Therefore, no need a loader for the view layer. You can use the view layer on the controller like the following example.

```php
return View::render($response, "sample.tpl", $params);
```
 
The first parameter contains $response variable, secondary parameter contains the template file name and the third parameter contains the data you wanted to pass to the view layer.
 
##### Getting configurations on the controller
 
You can get all of the configurations from the files on the app/config directory. If it is necessary, you can pass these configurations to the Model layer or other layers/structures.
 
There is an example of getting the app/config/database.php file configurations.
 
```php
$configuration['settings']['database']['default'] = [
    'driver' => 'mysql',
    'host' => 'localhost',
    'database' => '',
    'username' => '',
    'password' => '',
    'charset' => 'utf8',
    'collation' => 'utf8_unicode_ci',
    'prefix' => '',
];
```
 
Maybe you wanted to get a specific configuration variable, you can inspect the following example.
 
```php
$databaseInfo = Settings::get()['database']['default'];
```
 
##### Should you know

- The model, library and helper files should be loaded just on the controller files.
- You shouldn't perform operations such as getting data from the database, inserting data to the database, getting data from the API and getting data from the disk. These operations should be performed on the model and library files.