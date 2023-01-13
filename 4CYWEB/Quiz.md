# 1 
1. A LAMP webserver consists of:

Linux - The operating system

Apache - The webserver that serves http requests for html files, images, videos, and javascript, css and other files

MySQL - Is a database

PHP - Is the backend scripting 



2. JavaScript is used for front end scripting as it is the only language natively supported by a browser. 

However recently it has been made possible to run Python using PyScript that uses JavaScript in the browser to run Python code



3. PHP is the default backend scripting language in  a LAMP stack. However it is also possible to use Python, or, Perl (without changing the acronym)

# 2
1. A LAMP webserver consists of:

Linux - The operating system

Apache - The webserver that serves http requests for html files, images, videos, and javascript, css and other files

MySQL - Is a database

PHP - Is the backend scripting 



2. JavaScript is used for front end scripting as it is the only language natively supported by a browser. 

However recently it has been made possible to run Python using PyScript that uses JavaScript in the browser to run Python code



3. PHP is the default backend scripting language in  a LAMP stack. However it is also possible to use Python, or, Perl (without changing the acronym)
Comment:
LAMP architecture:

The physical layout of a web server is usually just one web server which has a database installed as well. You could have the database installed on another server if there is enough traffic.

# 3
1. 
Linux, Windows server,

NGINX, Apache, IIS

MySQL, MariaDBm Redis, Micrsoft SQL, MongoDB, noDB, Oracle

PHP, Python, Perl, Objective C, C#, Java, Go, Ruby on rails, Jquery, Django, .NET, asp.NET, angula.JS, expresss.JS, node.JS, X

Amazon 

API (JSON, or SOAP),



2. 

Load balancing

Dynamic webpages

Shared database / resources

Additional resources to process large data (CPU / RAM / storage), increased performance

Additional security / protection from attack

# 4
1. 
Linux, Windows server,

NGINX, Apache, IIS

MySQL, MariaDBm Redis, Micrsoft SQL, MongoDB, noDB, Oracle

PHP, Python, Perl, Objective C, C#, Java, Go, Ruby on rails, Jquery, Django, .NET, asp.NET, angula.JS, expresss.JS, node.JS, X

Amazon 

API (JSON, or SOAP),



2. 

Load balancing

Dynamic webpages

Shared database / resources

Additional resources to process large data (CPU / RAM / storage), increased performance

Additional security / protection from attack
![[Pasted image 20221029211518.png]]

#### Question 1 - Requests

**1. Start Line**

Includes 3 parts - method, URL, HTTP version

  

**2. HTTP Headers**

  

Case insensitive strings followed by a colon (:) then a value depending on the header

  

Each header is one line but can be very long

  

Multiple headers can be included each on its own line.

  

Types of headers include request, general, and, entity.

  

  

**3. Empty Line**

  

Denotes the change from headers to body

  

**4. Body**

  

GET, HEAD, DELETE, or OPTIONS, usually don't need a body 

  

#### Question 2 - Response

**1. Start Line**

Also called the status line

  

Includes HTTP Version, Status Code, Status Text

  

**2. HTTP Headers**

  

Case insensitive strings followed by a colon (:) then a value depending on the header

  

Each header is one line but can be very long

  

Multiple headers can be included each on its own line.

  

Types of headers include request, general, and, entity.

  

**3. Empty Line**

  

Denotes the change from headers to body

  

**4. Body**

  

Includes the requested information however some responses do not contain a body such as status code 201, or 204