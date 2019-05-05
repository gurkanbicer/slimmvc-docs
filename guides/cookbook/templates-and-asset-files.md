You can organize the templates in a sub-directory like the v1, v2, v3, fresh, minimal, etc. All of the sub-directories should be on the app/views directory. You can use the template files as nested with Smarty.
 
Also, you can organize the asset files (CSS, Images, Js, etc.) for these templates. 
 
For example, even if the interface of the website will never change; separating the visitor interface from the admin interface can make sense.
 
An example of the app/views directory tree:
 
```none
- app
 - views
  - v1
   - header.tpl
   - index.tpl
   - sidebar.tpl
   - post.tpl
   - footer.tpl
  + v2
  + v3
  + fresh
  + minimal
+ public
- index.php  
```
 
An example of the public/assets directory tree:
 
```none
+ app
- public
 - assets
  - v1
   - css
   - fonts
   - img
   - js
   - vendor
  + v2
  + v3
  + fresh
  + minimal
- index.php   
```
