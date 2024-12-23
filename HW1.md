#### Web 
    - An application that connects computers or machines over internet
#### Web Service 
    - An application that provides services over internet

A web service is a standardized way of enabling communication and data exchange between different applications or systems over the internet or a network. It allows applications to interact with each other regardless of the programming languages, platforms, or technologies they are built on. Web services enable interoperability by using open standards, such as HTTP, XML, SOAP, and REST, which ensure that data is transmitted in a consistent format across different systems.

#### Key Features of a Web Service:

##### Interoperability: 

Web services allow different systems and applications, possibly using different languages and platforms, to work together by providing a standardized communication protocol.
##### Platform Independence: 

Web services are platform-agnostic, meaning that they can be accessed from any device or operating system capable of making network requests.
##### Standardized Communication Protocols: 

Web services use standardized protocols like HTTP, XML, SOAP, and REST to ensure consistent and secure data exchange.

#### WSDL

Web Sevice Description Language. It is an XML based interface that is used to  describe the functionalities of Web services.
WSDL is an interface for web service consumer(client) and Web service provider(server) through which the fuctionalities of provider is communicated and used by consumer.

#### UDDI

Universal Description, Discovery and Integration. It is a platform for registering and discovering web services.

![WebService](pictures\Webservices.png)

#### SOAP

Simple Object Access Protocol.

##### SOAP API or SOAP Web Service

A SOAP API or SOAP Web Service is a protocol-driven approach to enabling communication between disparate systems over a network. Its reliance on XML, strict standards, and support for advanced features like security and transactions make it a powerful tool for building robust, enterprise-level web services. While it may be more complex and heavyweight compared to alternatives like REST, SOAP remains a critical technology in scenarios where formal contracts, interoperability, and comprehensive security are required.

A Web Service that complies to the SOAP Web Services Specification is a SOAP Web Service.

#### Key Characteristics of SOAP APIs

##### Protocol-Based:

SOAP is a protocol with strict standards and specifications. It defines a set of rules for structuring messages, ensuring consistency and reliability in communication.

##### XML-Based Messaging:

SOAP messages are formatted in XML, making them both platform- and language-independent.XML allows for complex data structures and type definitions, supporting sophisticated interactions.

##### Transport Protocols:

While SOAP can operate over various transport protocols (HTTP, SMTP, TCP, etc.), it is most commonly used with HTTP or HTTPS.

##### Extensibility:

SOAP supports additional standards for security (WS-Security), transactions, and more, allowing for enhanced features beyond basic message exchange.

##### Standardized Interface:

SOAP relies on WSDL (Web Services Description Language) to describe the service’s capabilities, operations, and how to interact with it.
WSDL acts as a contract between the service provider and the consumer, ensuring both parties understand the communication protocol.

#### Structure of a SOAP Message

A SOAP message is an XML document consisting of an Envelope, which contains a Header and a Body:

```
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Header>
    <!-- Optional header information -->
  </soap:Header>
  <soap:Body>
    <!-- The main content, such as request or response data -->
    <m:GetStockPrice xmlns:m="http://www.example.org/stock">
      <m:StockName>IBM</m:StockName>
    </m:GetStockPrice>
  </soap:Body>
</soap:Envelope>

```

* Envelope: Defines the start and end of the message and contains the Header and Body.
* Header: Optional element used for metadata like authentication, transactions, etc.
* Body: Contains the actual message intended for the recipient, such as request parameters or response data.

#### How SOAP Web Services Work


##### 1. Service Definition with WSDL:

* The service provider defines the web service using WSDL, which describes the available operations, the input and output parameters, and the binding details.

* Example WSDL snippet:
    ```
    <wsdl:definitions xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/"
                    xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
                    xmlns:tns="http://www.example.org/stock"
                    targetNamespace="http://www.example.org/stock">
    <wsdl:service name="StockService">
        <wsdl:port name="StockPort" binding="tns:StockBinding">
        <soap:address location="http://www.example.org/stockservice"/>
        </wsdl:port>
    </wsdl:service>
    <!-- More definitions -->
    </wsdl:definitions>

    ```

##### 2. Client Sends a SOAP Request:

* The client application constructs a SOAP XML message and sends it to the service endpoint defined in the WSDL.

* Example Request:
    ```
    <soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <m:GetStockPrice xmlns:m="http://www.example.org/stock">
                <m:StockName>IBM</m:StockName>
            </m:GetStockPrice>
        </soap:Body>
    </soap:Envelope>
    ```

##### 3. Service Processes the Request:

* The server receives the SOAP message, parses the XML, and invokes the appropriate service method based on the operation specified.

* It performs the necessary business logic, such as fetching the stock price for the given stock name.

##### 4. Service Sends a SOAP Response:

* After processing, the service constructs a SOAP response message containing the result.

* Example Response:
    ```

    <soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <m:GetStockPriceResponse xmlns:m="http://www.example.org/stock">
                <m:Price>150.00</m:Price>
            </m:GetStockPriceResponse>
        </soap:Body>
    </soap:Envelope>

    ```

##### 5. Client Receives and Processes the Response:

* The client parses the SOAP response, extracts the necessary information, and uses it within the application.



#### REST

Representational State Transfer

##### RESTful Web Services

RESTful Web Services implement the REST architecture to allow communication between systems over the web. These services expose resources (e.g., data objects or functions) that clients can interact with using HTTP methods.

RESTful services provide a lightweight, scalable, and flexible means for applications to communicate over HTTP by simply using its verbs (GET, POST, PUT, DELETE, etc.) and responding with representations (typically in JSON or XML).

#### Key Features of RESTful Web Services:

##### 1. Use of Standard HTTP Methods:

* GET: Retrieve data from a server (read-only).
* POST: Create new resources on the server.
* PUT: Update an existing resource on the server.
* DELETE: Remove a resource from the server.
* PATCH: Update partial content of a resource.

##### 2. Resource Identification via URI:

* Resources in REST are identified by URIs (Uniform Resource Identifiers). For example, a resource representing a book might be accessible at:

    ```

    https://api.example.com/books/OCI3Integration

    ```
    In this case, OCI3Integration identifies a specific book.

##### 3. Representation of Resources:

* Resources are represented in various formats, commonly JSON or XML. The client requests the format it prefers using the Accept header, and the server provides the appropriate representation.
* Example JSON representation of a book:
    ```
    {
        "id": OCI3Integration,
        "title": "Learning OCI3Integration",
        "author": "John Doe",
        "published": "2021"
    }
    ```
##### 4. Stateless Communication:

* RESTful services are stateless, meaning that every request from the client must contain all the information needed by the server to fulfill the request. The server does not store any session data between requests.

##### 5. Caching:

* REST allows responses to be cacheable. This can significantly improve the performance of web applications by reducing server load and client-side latency.
* For example, static resources like images or articles can be cached by the client.

##### 6. Layered System:

* RESTful systems can be designed with layers of servers, with responsibilities distributed across multiple layers. For instance, a proxy server can intercept and forward client requests to the actual server.

#### Example of a RESTful Web Service

Let’s consider an API for managing books in a library. The server provides different URIs for each resource (like books) and supports various HTTP methods to manipulate them.

##### 1. GET Request (Read a book resource):

```
    GET /api/books/123
```

Response:

```
{
  "id": 123,
  "title": "Learning REST",
  "author": "John Doe",
  "published": "2021"
}
```

##### 2. POST Request (Create a new book resource):

```
POST /api/books
```

Request Body (JSON):

```
{
  "title": "New Book",
  "author": "Jane Smith",
  "published": "2023"
}
```

Response:

```
{
  "id": 124,
  "title": "New Book",
  "author": "Jane Smith",
  "published": "2023"
}
```

##### 3. PUT Request (Update an existing book resource):

```
PUT /api/books/124
```

Request Body:

```
{
  "title": "Updated Book",
  "author": "Jane Smith",
  "published": "2023"
}
```

Response:

```
{
  "id": 124,
  "title": "Updated Book",
  "author": "Jane Smith",
  "published": "2023"
}

```

##### 4. DELETE Request (Remove a book resource):


```
DELETE /api/books/124
```

Response:

```
{
  "message": "Book deleted successfully."
}
```

#### OAuth

"Open Authorization"

#### OAuth Token

An OAuth token is a credential used in the OAuth (Open Authorization) framework to grant limited access to a user’s resources on a server without exposing their credentials (like username and password). OAuth tokens enable applications (clients) to access resources hosted by another service (resource server) on behalf of a user, following the user's authorization.

#### Key Components of OAuth

###### 1. Resource Owner: 
    Typically the end-user who owns the data or resources.

###### 2. Client:
    The application requesting access to the resource owner’s data.

###### 3. Resource Server:
    The server hosting the user’s data (e.g., Google, Facebook).

###### 4. Authorization Server:
    The server that authenticates the resource owner and issues tokens to the client (often the same as the resource server).



