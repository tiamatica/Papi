# Papi

Papi is an OpenAPI toolkit for Dyalog APL to generate API clients and servers from OpenAPI descriptions. It allows compiling OpenAPI JSON schemas into APL classes to help consume RESTful web services. It can also be used to generate server stubs to act as a server.

## How to use it

TODO: Papi is a Tatin package and can be loaded or installed via Tatin:  

```apl
]TATIN.LoadPackages tiamatica-Papi
```  

## As a client

To generate classes from OpenAPI schemas, call the `Compile` function. It requires two arguments: the path to the directory containing the OpenAPI descriptions and the path to the directory where you want to place the compiled classes.

```apl
Papi.Compile <'path/schemadir'> <'path/clientdir'> 
```  
This generates a folder for each json schema and a class for each endpoint operation. After importing the new directory you can easily call the API using these classes. All you need is an instance of HttpCommand. A description of the specific arguments needed for the function can be found as comments in the class.

```apl
res←clt Petstore.FindPetById.Run 3
```  

This returns a three item vector. If all went well the data is returned as a JSON object.:

```apl
0 200  [JSON object]
``` 

## As a server


```apl
Papi.CompileServer <'path/schema.json'> <'path/serverdir'> 
``` 


## More

More detailed documentation can be found [here](./docs/documentation.md).
