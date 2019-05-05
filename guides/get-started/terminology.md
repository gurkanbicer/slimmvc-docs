We wanted to explain mostly used terms on this page.

##### What is MVC?

**MVC** is the most preferred design pattern. **MVC** is an abbreviation for Model, View, and Controller.

##### The Model

The model is the data layer on the **MVC** design pattern. It provides data transfer between the app and the database or the other data sources.

##### The View

The view is the interface layer on the **MVC** design pattern. It provides an interface with or without returned data from the model layer.

##### The Controller

The controller is the control layer on the **MVC** design pattern. It manages Model and View layers. 

##### The Route

The route is a helper layer for **MVC** design pattern. It determines to route to the Controllers for incoming requests sent by the client.

##### The Request

The request is the information sent by the client to the server.

##### The Response

The response is the information sent by the server to the client.

##### MVC’s workflow

Let’s think about a book website and let’s assume a client reaching to the history books on this website. **MVC** will apply the following workflow:

- The route will determine which controller file should run.
- The controller file will load the related model file(s). 
- The controller file will forward the parameters sent by the route layer to the model file(s).
- The model files(s) will collect data from the database or other sources, and the data will be returned to the controller file.
- The controller file will determine which template file will be rendered on the view layer.
- The controller file will forward the template file name and the data to the view layer.
- The view layer will render the template with the data, and it will be returned to the controller file.
- The controller file will respond to the client with this interface when all of the workflows is ended.

##### The Library

The library is an independent structure from the **MVC** design pattern. But, it's similar to the model layer and it's flexible about the using purposes. The most important purpose is integrating with 3rdparty dependencies that cannot be loaded by the Composer. Also, the library structure can data transfer like the model layer. Or, it can be a tool for data transfer.

##### The Helper

The helper is an independent structure from the **MVC** design pattern. But, it can be used on the Controller and Model layers. Some of using purposes are filtering, securing and processing the data sent by Model, View, and Route layer. 

Apart from other structures, the helper files only contain functions, not contains classes.

##### The Middleware 

The middlewares are the independent structure from the **MVC** design pattern. It can be used with controller files and routes. It runs before and after the controllers. It's similar to hooks.

##### The Facade 

The facade is an independent structure from the **MVC** design pattern. It can call classes and objects as statically.

##### The Dependency Injection (DI)

Dependency Injection ensures that your classes or packages and your own classes and packages work in harmony with your current design pattern.

The Dependency Container is the main object in which these classes and packages are collected.

##### The Important note

Some terms may have different meanings in different programming languages. In the same programming language, a specific action can be defined in different terms. The information on this page may not equal overlap 100% with each source. For this reason, it is useful to investigate more than one source to get more information and to understand the purposes of the terms.
