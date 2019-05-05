We have mentioned about the giving names to routes and using it for dynamic linking within template files. You can see how it will be done on the below.
 
You can get the link with the path_for function that integrated to Smarty.
 
###### Example of a route:
 
```php
Route::get('/books', '\booksController:index')->setName('booksIndex');
```
 
###### Example of a template file:
 
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Sample Page</title>
        <meta name="charset" content="utf-8">
        
        <!-- style -->
        <!-- js -->
    </head>
    <body>
        <a href="{path_for name='booksIndex'}">Books</a>
    </body>
</html>
```
 
###### Another an example of a route:
 
```php
Route::get('/books/{category}', '\booksController:category')->setName('booksCategoryIndex');
```
 
###### Another an example of a template file:
 
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Sample Page</title>
        <meta name="charset" content="utf-8">
        
        <!-- style -->
        <!-- js -->
    </head>
    <body>
        <a href="{path_for name='booksIndex' data=['category' => 'history']}">History Books</a>
    </body>
</html>
```
 
When you update your route files any day, you won't need to edit the template files.
