The view layer using the [Smarty](https://www.smarty.net/) template engine. You can get more information about the Smarty on the Smarty Documents [page](https://www.smarty.net/docs/en/).
 
##### Creating a template file
 
All of the template files should be in the app/views directory and all of the files should be “.tpl” extension. Also, you can categorize your template files like the “v1, v2, fresh, minimal, etc.) with sub-directories.
 
##### An example of a template
 
The following example assumes $name and $age variables passed into the view layer.
 
```html
<!DOCTYPE html>
<html>
  <head>
    <title>{$pageTitle}</title>
    <meta name="UTF-8">

    <style type="text/css">
      html, body {
        font-size: 18px;
        font-weight: 400;
      }
    </style>
  </head>
  <body>
    Name : {$name}<br>
    Age : {$age}
  </body>
</html>
```
 
##### Using view on the controller
 
The view layer is loading automatically in the beginning. Therefore, no need a loader for the view layer. You can use the view layer on the controller like the following example.
 
```php
  public function getPerson(Request $request, Response $response, $args) {
    $params = [
      'name' => $args['name'],
      'age' => $args['age'],
    ];
    return View::render($response, "sample.tpl", $params);
  }
```
 
The first parameter contains $response variable, secondary parameter contains the template file name and the third parameter contains the data you wanted to pass to the view layer.
 
##### An example of a quick start
 
There are examples for defining a route, creating a controller file, and creating a template file.
 
###### Example for a route:
 
```php
Route::get('/person/{name}/{age}', '\sampleController:getPerson');
```
 
###### Example for a controller:
 
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

  public function getPerson(Request $request, Response $response, $args) {
    $params = [
      'name' => $args['name'],
      'age' => $args['age'],
    ];
    return View::render($response, "sample.tpl", $params);
  }

}

/* path: ~app/controllers/sampleController.php */
```
 
###### Example for a template:
 
```html
<!DOCTYPE html>
<html>
  <head>
    <title>{$pageTitle}</title>
    <meta name="UTF-8">

    <style type="text/css">
      html, body {
        font-size: 18px;
        font-weight: 400;
      }
    </style>
  </head>
  <body>
    Name : {$name}<br>
    Age : {$age}
  </body>
</html>
```

