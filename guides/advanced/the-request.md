You can inspect every request sent by the client to the server on the Slim PHP Extended and you can manipulate it. You can reach this information on the controller or middleware.
 
##### Getting The Request Method
 
You can get the request method like the following example.
 
````php
$method = $request->getMethod();
````
 
Also, you can check the request method with the following functions.
 
```php
$isGet = $request->isGet();
$isPost = $request->isPost();
$isPut = $request->isPut();
$isDelete = $request->isDelete();
$isHead = $request->isHead();
$isPatch = $request->isPatch();
$isOptions = $request->isOptions();
```
 
These functions will return boolean _(true/false)_ data.
 
##### Getting The Request URI
 
You may want to get more information about the request. You can get the request URI details like the following example. It will return the host, port, path, and query string data.
 
```php
$uri = $request->getUri();
```
 
Also, you can get specific information from the request URI like the following example.
 
```php
$scheme = $request->getScheme();
$authority = $request->getAuthority();
$userInfo = $request->getUserInfo();
$host = $request->getHost();
$port = $request->getPort();
$path = $request->getPath();
$basePath = $request->getBasePath();
$query = $request->getQuery();
$fragment = $request->getFragment();
$baseUrl = $request->getBaseUrl();
```
 
##### Getting The Request Headers
 
You may want to get request header information. You can get this information like the following example.
 
```php
$headers = $request->getHeaders();
foreach ($headers as $name => $values) {
    echo $name . ": " . implode(", ", $values);
}
```
 
##### Getting The Request Body
 
The client can send data to the server. It can be POST data, JSON data or XML data. You can reach these data like the following example. 
 
```php
$parsedBody = $request->getParsedBody();

```
 
You can visit Slim Framework original [document](http://www.slimframework.com/docs/v3/objects/request.html) for getting more information. 
