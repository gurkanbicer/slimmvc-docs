##### Creating a Helper
 
All of the helper files should be on the app/helpers directory. The helper file should be named like **xxxHelper** for project entirety. The helper files not contain classes, it just contains functions. 
 
##### An example of a helper
 
In the following example, there are functions to formatting the data in a generated HTML output.
 
```php
<?php

  function hTagFormatter($text, $classes = "") {
      return preg_replace('/<h([0-9])>/i', '<h$1 class="'.$classes.'">', $text);
  }

  function pTagFormatter($text, $classes = "") {
      return preg_replace('/<p>/i', '<p class="'.$classes.'">', $text);
  }

  function preTagFormatter($text, $classes = "") {
      return preg_replace('/<pre>/i', '<pre class="'.$classes.'">', $text);
  }

/* path: ~app/helpers/formatterHelper.php */
```
 
##### Some of using purposes
- Securing the data
- Filtering the data
- Processing the data
