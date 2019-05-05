##### Creating a model
 
All of the model files should be in the app/models directory. The model file should be named like the **xxxModel** for project entirety. The file name and the class name inside this file should be same.
 
There is an example of the model file.
 
```php
<?php

    Class sampleModel {

        private $c;

        public function __construct($container) {
            $this->c = $container;
        }

        public function sample($params = []) {
            // bla bla bla
        }

    }

/* path: ~app/models/sampleModel.php */
```
 
##### An example of a model
 
A facade named Database, which uses the illuminate/database package is used on the following example.
 
```php
<?php
use SlimFacades\Database;

    Class sampleModel {

        private $c;

        public function __construct($container) {
            $this->c = $container;
            Database::connectTo('default');
        }

        public function getSampleData($params = []) {
            return Database::table('sampleTable')
              ->where('id', '=', $params["id"])
              ->toArray();
        }

    }

/* path: ~app/models/sampleModel.php */
```

##### Using models on the Controller
 
Firstly, the model should be defined in the __construct() function of the controller. You can inspect the following example.
 
```php
public function __construct($container) {
    $this->c = $container;
    Model::load('sample');
}
```
 
Any function in the model file can be called like the following example.

```php
$results = Container::get('sampleModel')->getSampleData(['id' => 5]);
```
 
##### Using helpers on the Model
 
Firstly, the helper should be defined in the __construct() function of the controller. You can inspect the following example.
 
```php
public function __construct($container) {
    $this->c = $container;
    Helper::load('sample');
}
```
 
Any function in the helper file can be called on the model like the following example.
 
```php
$text = pTagFormatter($text, 'text-muted mx-3');
```
