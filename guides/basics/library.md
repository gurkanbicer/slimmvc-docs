##### Creating a Library
 
All of the library files should be on the app/libraries directory. The library file should be named like **xxxLibrary** for project entirety.  The file name and the class name inside this file should be same. The library files need their own directory. Those directories should be named without “Library” suffix.
 
An example of a directory tree:
 
```none
  - app
    - libraries
      - xxx
        - xxxLibrary.php
        - config.php
        + anyDirectoryInside
      - yyy
        - yyyLibrary.php
      - zzz
        - zzzLibrary.php
```

##### An example of a library 

```php
<?php

	Class sampleLibrary {

		private $c;

		public function __construct($container) {
          $this->c = $container;
		}

		public function sampleAction($params = []) {
          return $params[0] * $params[1];
		}

	}

/* path: ~app/libraries/sample/sampleLibrary.php */
```

##### Some of using purposes
- Integrating 3rdparty dependencies
- Data transfer
- Remote API’s
- The other needs etc.