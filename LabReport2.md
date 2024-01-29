# **Lab Report 2**

Pranav Reddy Bussannagari
***


## Code for ChatServer
![CodeChatServer](CodeChatServer.png)


## Screenshot 1
![ChatServerUse](ChatServerUse.png)

> ## Methods from my code

> `Server.start(int port, new Handler())`;
-   Arguments: integer value for which port to listen on, Handler object
-   No values changed as this function just starts a server on the local computer
> Default Constructor for `Handler` class
-   Arguments: none
-   The `String chatHistory` is created, which will be used to add the formatted message onto the webpage
> `handleRequest(URI url)` from `Handler` class
-   Arguments: `URI url` 
-   If the proper path is provided, updates `String chatHistory` with the formatted message to be printed onto the webpage
> `main(String[] args)` from `ChatServer`
-   Arguments: `String[] args`, specifically an Integer to be parsed into being the port number
-   Updates `port` with the number passed in, provided a valid number for the computer to be listening on is provided

> ## Other methods executed

> `getPath()`
-   Arguments: none
-   Updates no variable directly as it checks if the url's path contains specific keywords to return the correct page.
> `getQuery()`
-   Arguments: none
-   Updates no variable directly, but returns the query string (after the `?`) to be placed into the main `parameters String array`, which is later split into other arrays.


## Screenshot 2
![ChatServerUse2](ChatServerUse2.png)

> `Server.start(int port, new Handler())`;
-   Arguments: integer value for which port to listen on, Handler object
-   No values changed as this function just starts a server on the local computer
> Default Constructor for `Handler` class
-   Arguments: none
-   The `String chatHistory` is created, which will be used to add the formatted message onto the webpage
> `handleRequest(URI url)` from `Handler` class
-   Arguments: `URI url` 
-   If the proper path is provided, updates `String chatHistory` with the formatted message to be printed onto the webpage
> `main(String[] args)` from `ChatServer`
-   Arguments: `String[] args`, specifically an Integer to be parsed into being the port number
-   Updates `port` with the number passed in, provided a valid number for the computer to be listening on is provided

> ## Other methods executed

> `getPath()`
-   Arguments: none
-   Updates no variable directly as it checks if the url's path contains specific keywords to return the correct page.
> `getQuery()`
-   Arguments: none
-   Updates no variable directly, but returns the query string (after the `?`) to be placed into the main `parameters String array`, which is later split into other arrays.


## Part 2

