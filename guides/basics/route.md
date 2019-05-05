**Slim Framework** and **SlimMVC** uses **nikic/fastroute** package for the routing process.
 
We did gather all of the routes into a single file named app/core/routes.php. In addition, we prepared a core file for automatically loading controller files.
 
When you want to create a route, you should open the app/core/routes.php file and you should add a route like the following. 
 
```php
Route::get('/', '\homeController:index')->setName('indexPage');
```

The first parameter contains URL, secondary parameter contains the controller name and function name. The controller name and function name must be separated with “:” character.

_**The important note:** There is case-sensitivity. You should write the controller name and function name as correctly._
 
##### The GET route

You can create a GET route like the following.

```php
Route::get('/books', '\booksController:getBooks');
```

##### The POST route

You can create a POST route like the following.
 
```php
Route::post('/books/set/{id}', '\booksController:setBook');
```

##### The PUT route

You can create a PUT route like the following.

```php
Route::put('/books/put', '\booksController:addBook');
```

##### The DELETE route

You can create a DELETE route like the following.

```php
Route::delete('/book/{id}', '\booksController:delBook');
```

##### The OPTIONS route

You can create a OPTIONS route like the following.

```php
Route::options('/book/{id}', '\booksController:sampleAction');
```

##### The PATCH route

You can create a PATCH route like the following.

```php
Route::patch('/book/{id}', '\booksController:sampleAction');
```

##### The ANY route

You can create an ANY route for any type of request like the following.

```php
Route::any('/book/{id}', '\booksController:sampleAction');
```

##### The MAP 

You can create a MAP route for defined types of the request like the following.

```php
Route::map(['GET', 'POST'], '/book/{id}', '\booksController:sampleAction');
```

##### Redirecting with route

You can create a route for 301 and 302 redirecting.

```php
Route::redirect('/old-url', '/newUrl', 301);
```

##### Giving a name to route

You can give names to routes. Also, you can use these names for dynamic linking on the templates.

```php
Route::get('/books', '\booksController:getBooks')->setName('getBooksPage');
```

##### Adding middleware to routes

You can add middleware to the route. If you want to get more information about the middlewares, you can inspect the Middlewares page.

```php
Route::get('/books', '\booksController:getBooks')
  ->setName('getBooksPage')
  ->add( new sampleMiddleware() );
```
 
##### Using regex
 
You can use Regex on the routes like the following. 
 
```php
Route::get('/users/{id:[0-9]+}', '\userController:getUser');
```
 
You can visit the **Slim Framework** original [document](http://www.slimframework.com/docs/v3/objects/router.html) to get more information.