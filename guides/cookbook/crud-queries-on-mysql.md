CRUD is an abbreviation of Create, Read, Update, and Delete. When you connected to the database, you can perform these operations.
 
##### Insert Query (Create)
 
The following example assumes that there is a table named users and inserts data to this table.
 
```php
$insertData = [
    'name' => 'Gurkan',
    'surname' => 'Biçer',
    'age' => 23,
];
$insertId = Database::table('users')
    ->insertGetId($insertData);
```
 
##### Select Query (Read)
 
The following example assumes that there is a table named users and getting all data from this table.
 
```php
$results = Database::table('users')->get();
```
 
The following example is to get first row data by the condition.
 
```php
$result = Database::table('users')
    ->where('id', '=', 5)
    ->first();
```
 
The following example is using on the pagination usually.
 
```php
$result = Database::table('users')
    ->skip(0)
    ->limit(30)
    ->get();
```
 
##### Update Query
 
The following example assumes that there is a table named users and that data is updating by the condition. 
 
```php
$update = Database::table('users')
    ->where('id', '=', 5)
    ->update([
        'age' => 24
    ]);
```
 
##### Delete Query
 
The following example assumes that there is a table named users and that data is deleting by the condition. 

```php
$update = Database::table('users')
    ->where('id', '=', 5)
    ->delete();
```
 
##### More information
 
Of course, we would like to include all the examples that you can use in our documents. We would like to include all the samples you need, such as queries using "Inner Join", the use of "Order By", "Skip" and "Limit". However, the most detailed information about a subject is learned better than its own documentation. For this reason, we have shared the documentation link of the related package until we have arranged our documents to help you further.
 
You can visit the **illuminate/database** package original [document](https://laravel.com/api/5.3/Illuminate/Database/Query/Builder.html) to get more information.
