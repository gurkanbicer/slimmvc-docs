You can inspect every response sent by the server on the Slim PHP Extended and you can manipulate it. You can reach this information on the controller or middleware.
 
##### Getting the response status
 
You can get response status code returned by the server like the following example.
 
```php
$status = $response->getStatusCode();
```
 
You can set response status code before responding to the client like the following example.
 
```php
$newResponse = $response->withStatus(302);
```
 
##### Getting the response headers
 
You can get response headers like the following codes.

```php
$headers = $response->getHeaders();
foreach ($headers as $name => $values) {
    echo $name . ": " . implode(", ", $values);
}
```
 
You can set response headers before responding to the client like the following example.
 
```php
$response = $response->withHeader('Content-type', 'application/json');
```
 
##### Getting the response body
 
You can get response body like the following example.
 
```php
$body = $response->getBody();
```
 
You can set the response body before responding to the client like the following example.
 
```php
$body = $response->getBody();
$body->write('Hello');
```
 
##### Responding with JSON
 
You can return a JSON string with application/json mime type.
 
```php
$data = array('name' => 'Bob', 'age' => 40);
return $response->withJson($data);
```
 
##### Redirecting on the response
 
You can redirect the client to another URL like the following example.
 
```php
return $response->withRedirect('/new-url', 301);
```

You can visit Slim Framework original [document](http://www.slimframework.com/docs/v3/objects/response.html) for getting more information. 

