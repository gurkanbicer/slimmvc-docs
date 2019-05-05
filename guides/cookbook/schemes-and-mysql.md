Some of the frameworks contain the migration feature. You can create the tables on the MySQL and you can insert sample data on those tables. A lot of projects needs this feature. Therefore, we prepared a sample using the Schemes feature of illuminate/database package.
 
You can do it on your own project step by step like the following.
 
##### Creating a route
 
You should create a route like the “/migrate/{action}” or “/scheme/{action}”. It’s up to you. Here is an example:
 
```php
Route::get('/migrate/{action}', '\migrateController:index');
```
 
##### Creating a controller
 
The controller file used by the above example like the following.
 
```php
<?php
use Psr\Http\Message\ServerRequestInterface as Request;
use Psr\Http\Message\ResponseInterface as Response;
use SlimFacades\Container;
use SlimFacades\Model;

	Class migrateController {

		private $c;

		public function __construct($container) {
			$this->c = $container;
			Model::load('migrate');
		}

		public function index(Request $request, Response $response, $args) {
			switch ($args['action']) {
			    case 'make':
			        $result = Container::get('migrateModel')->make();
			        if ($result === false)
			            return $response->getBody()->write('Migrate action failed.');
			        else
			            return $response->getBody()->write('Migrate action successful.');
			        break;
			    case 'drop':
			        $result = Container::get('migrateModel')->drop();
			        if ($result === false)
                    	return $response->getBody()->write('Migrate action failed.');
			        else
                    	return $response->getBody()->write('Migrate action successful.');
			        break;
			        
			    default:
			        return $response->getBody()->write('An undefined value has been entered.');       
			}
		}

	}

/* path: ~app/controllers/migrateController.php */
```
 
##### Creating a model
 
The model file used by the controller like the following.
 
```php
<?php
use SlimFacades\Database;

	Class migrateModel {

		private $c;

		public function __construct($container) {
			$this->c = $container;
			Database::connectTo('default');
		}

		public function make() {
			// bla bla bla
			
			return true;
		}
		
		public function drop() {
		    // bla bla bla
		    return true;
		}

	}

/* path: ~app/models/sampleModel.php */
```
 
##### make() function 
 
You can create, edit, delete tables, and insert sample data to those tables on the make() function. The following example checks if a table exists and creates a table if it does not exist.
 
```php
public function make() {
    if (Database::schema()->hasTable('users') === false) {
        Database::schema()->create('users', function ($table) {
            $table->increments('id');
            $table->string('name');
            $table->string('email')->unique();
            $table->string('password');
            $table->string('userimage')->nullable();
            $table->string('api_key')->nullable()->unique();
            $table->rememberToken();
            $table->timestamps();
        });
    }
}
```
 
##### drop() function
 
You can delete tables on the drop() function. The following example checks if a table exists and deletes a table if it does exist.

```php
public function drop() {
    Database::schema()->dropIfExists('users');
    return true;
}
```

##### The important note
 
Other frameworks need a mechanism such as version control for migration. Since this migration feature is not a feature that comes directly from within SlimPHP Extended and our goal is to create the database design of our application from application codes using the illuminate/database package, we haven’t created an external core file. This document has just compared the schema logic to the migration feature to better describe it.
 
##### More information
 
You can visit the **illuminate/database** package original [document](https://laravel.com/docs/5.7/migrations) to get more information.