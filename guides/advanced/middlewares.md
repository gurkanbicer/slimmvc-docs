##### Creating a middleware
 
All of the middleware files should be on the app/middlewares directory. The middleware file should be named like xxxMiddleware for project entirety.  The file name and the class name inside this file should be same.
 
##### An example of a middleware
 
```php
<?php

    Class sampleMiddleware {
        public function __invoke($request, $response, $next) {
            $response->getBody()->write('BEFORE');
            $response = $next($request, $response);
            $response->getBody()->write('AFTER');
            return $response;
        }
    }
    
/* path: ~app/middlewares/sampleMiddleware.php */
```
 
##### Using middlewares
 
You should define the middleware into routes. You can inspect the following example.

```php
Route::get('/sample-page', '\sampleController:sampleFunction')
    ->add( new sampleMiddleware() );
```

##### Some of using purposes
- Sessions
- Security
- Logging
- The other needs etc.
