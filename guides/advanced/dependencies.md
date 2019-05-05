##### Dependency injection
 
All of the packages installed via Composer loaded automatically. Therefore, when you want to inject a dependency on the container, there is no additional operation. You can inject a dependency like the following example.

```php
$container['samplePackage'] = function() {
	$samplePackageRef = new samplePackage();
	return $samplePackageRef;
};
```
 
If you prepared a core file and want to inject to the container, firstly you should include this file app/core/autoload.php or app/core/dependencies.php file.
 
```php
require_once DIR_CORE . '/samplePackage.php';
```
 
##### Using dependencies on the Controller and Model
 
You can use dependencies on the controller and model layers. But, you should add the following code to the top of your file.
 
```php
use SlimFacades\Container;
```
 
You can call any functions from the dependency like the following example.
 
```php
$sampleData = Container::get('samplePackage')->sampleFunction();
```