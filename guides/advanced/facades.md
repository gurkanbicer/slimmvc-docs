##### Creating a facade
 
All of the facade files should be on the app/facades directory. The facade file should be named like xxxFacade for project entirety. The class inside the file should be named without “Facade” suffix and the class should be extended with “Facade” class. After then, the facade file should be included in the app/core/facades.php file.
 
##### An example of a facade
 
In the following example, a facade is created for a class that is assumed to be injected into the Dependency Container.
 
```php
<?php
namespace SlimFacades;

    Class Sample Extends Facade {

        public static function self() {
            return self::$app->getContainer()->get('samplePackage');
        }

    }

/* path: ~app/facades/sampleFacade.php */
```
 
##### Using facade
 
Firstly, you should define the facade on top of your file like the following example.
 
```php
use SlimFacades\Sample;
```
 
After then, you can call the functions inherited by the facade like the following example.

```php
Sample::sampleFunction();
```
