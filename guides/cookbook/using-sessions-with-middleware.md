You can use sessions on the controllers or models. But, optimal use area is middleware. Because middleware can be run before and after the controllers.
 
Firstly, you don't need to use session_start() function. We did add it into a core file. You should create data on the $_SESSION variable and check it.
 
##### An example middleware for sessions
 
The following example checks the created session data. if no data is available, the visitor redirecting to the "/login" page.
 
```php
<?php
use SlimFacades\Container;

    Class sessionMiddleware {

        public function __invoke($request, $response, $next) {

            if ($_SESSION['sampleSession'] !== true) {
                return $response->withStatus(302)->withHeader('Location', '/login');
            }

            $response = $next($request, $response);
            return $response;
            
        }
    }

/* path: ~app/middlewares/sessionMiddleware.php */
```
 
##### Defining middleware to a route
 
You can define the middleware to a route like the following.
 
```php
Route::get('/dashboard', '\dashboardController:index')->add( new sessionMiddleware() );
```
 
##### The other steps
 
This document contains an example of session checking on middleware. You need a login page and a session page that controls the user name and password that the visitor enters.
