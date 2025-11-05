## Q. What is Web API? What is the purpose of Web API?

What is Web API?**

Web API (Application Programming Interface) is a framework that allows you to build HTTP-based services that can be accessed by different clients — such as browsers, mobile apps, desktop apps, or other servers — over the web.

In the .NET world, ASP.NET Web API is the framework used to create RESTful services using HTTP.

**Purpose of Web API**

The main purpose of a Web API is to enable communication and data exchange between systems through standard web protocols.

**Key Purposes:**
1. **Data Sharing:**
Share data between different applications or platforms (e.g., web and mobile).
2. **Interoperability:**
Allow systems built in different languages or technologies to work together.
3. **Scalability:**
APIs can serve many clients simultaneously and independently.
4. **Reusability:**
The same API can be used by web, mobile, and desktop applications.
5. **Integration:**
Connect with third-party services (e.g., payment gateways, Google Maps, weather APIs).
6. **Separation of Concerns:**
Keeps the frontend (UI) and backend (data and logic) independent.


## Q. What are HTTP verbs or HTTP methods?
HTTP verbs (also called HTTP methods) are actions that tell a web server what operation to perform on a given resource (like data in a database) over the HTTP protocol.

They are fundamental to how Web APIs and RESTful services work.

**Most Common HTTP Methods**

| **Method**  | **Action**     | **Description**                                     | **Typical Use**                  |
| ----------- | -------------- | --------------------------------------------------- | -------------------------------- |
| **GET**     | Read           | Retrieves data from the server.                     | Fetch data (e.g., list of users) |
| **POST**    | Create         | Sends data to the server to create a new resource.  | Add a new record                 |
| **PUT**     | Update         | Updates or replaces an existing resource.           | Update an existing record        |
| **PATCH**   | Partial Update | Updates part of an existing resource.               | Modify specific fields           |
| **DELETE**  | Delete         | Removes a resource from the server.                 | Delete a record                  |
| **HEAD**    | Metadata       | Similar to GET, but returns only headers (no body). | Check if resource exists         |
| **OPTIONS** | Capabilities   | Returns supported HTTP methods for a resource.      | Check what actions are allowed   |

## Q. What is the difference Rest API and Web API?
**1. Web API (General Term)**

A Web API (Application Programming Interface) is a broad concept that refers to any API that can be accessed over the web using HTTP/HTTPS.

It allows applications to communicate or exchange data using web technologies — regardless of whether it follows REST or not.

***Every REST API is a Web API, but not every Web API is RESTful.***

**Example of a Web API**

A Web API could use:

- REST (Representational State Transfer)
- SOAP (Simple Object Access Protocol)
- GraphQL
- Or even custom HTTP-based designs

**2. REST API (Specific Type of Web API)**

A **REST API** is a type of **Web API** that follows the **REST architectural principles** defined by Roy Fielding.

**REST** stands for **Representational State Transfer** — it’s a design style that uses standard **HTTP methods** (GET, POST, PUT, DELETE) and works with **resources** represented as URLs.

```
GET https://example.com/api/students/1
```

Returns the data (usually in JSON) for student with ID 1.

**3. Key Differences Between Web API and REST API**
| **Feature**           | **Web API**                                                     | **REST API**                                                                  |
| --------------------- | --------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| **Definition**        | A service that exposes data or functionality over HTTP.         | A Web API that strictly follows REST principles.                              |
| **Architecture**      | Can be **REST**, **SOAP**, **GraphQL**, or **custom**.          | Must follow **REST architecture**.                                            |
| **Protocol**          | Typically uses **HTTP/HTTPS**, but may use other protocols too. | Uses only **HTTP/HTTPS**.                                                     |
| **Data Format**       | Can return **JSON**, **XML**, **HTML**, etc.                    | Commonly returns **JSON** (sometimes XML).                                    |
| **Design Rules**      | No strict rules — up to the developer.                          | Must follow **REST constraints** (Stateless, Client-Server, Cacheable, etc.). |
| **Statefulness**      | Can be **stateful or stateless**.                               | Must be **stateless** — no session is stored on the server.                   |
| **Example Framework** | ASP.NET Web API (can create REST or non-REST services)          | RESTful API built using ASP.NET Web API or any REST-compliant framework.      |


## Q. What are REST guidelines? What is the difference between Rest and Restful?
**1. REST Guidelines / Principles**

A service is considered RESTful only if it follows the six architectural constraints (guidelines) defined by REST.

| **#**            | **REST Constraint**            | **Description**                                                                                                                   | **Example / Meaning**                                       |
| ---------------- | ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| **1**            | **Client–Server Architecture** | The client (frontend/UI) and the server (backend/database) are separate.                                                          | The browser requests data; the server responds with JSON.   |
| **2**            | **Statelessness**              | Each request from client to server must contain all information needed to process it. The server does **not store session data**. | The server does not remember previous requests.             |
| **3**            | **Cacheable**                  | Responses must define whether they can be cached to improve performance.                                                          | E.g., “Cache-Control: max-age=600” in HTTP headers.         |
| **4**            | **Uniform Interface**          | Consistent way of accessing resources (using URIs, HTTP verbs, etc.).                                                             | `/api/products/1` always refers to the same product.        |
| **5**            | **Layered System**             | The API architecture may have multiple layers (security, caching, load balancer), and clients shouldn’t care.                     | Client only interacts with API endpoint, not inner systems. |
| **6 (Optional)** | **Code on Demand**             | Server can send executable code (like JavaScript) to the client.                                                                  | Rarely used in APIs today.                                  |

**2. REST Design Guidelines (Best Practices)**

Apart from the six formal constraints, developers also follow best practices when designing REST APIs:

| **Aspect**                  | **Guideline / Example**                                                               |
| --------------------------- | ------------------------------------------------------------------------------------- |
| **Resource Naming**         | Use **nouns** not verbs → `/api/users`, `/api/products`                               |
| **HTTP Methods**            | Use verbs for actions → GET, POST, PUT, DELETE                                        |
| **Stateless Communication** | Don’t store client session on the server                                              |
| **HTTP Status Codes**       | Use standard responses → 200 (OK), 201 (Created), 404 (Not Found), 500 (Server Error) |
| **Data Format**             | Return data in **JSON** (or XML)                                                      |
| **Versioning**              | Include API version in URL → `/api/v1/products`                                       |
| **Use Plural Nouns**        | `/api/users`, not `/api/user`                                                         |
| **Error Handling**          | Return structured error responses (with messages and codes)                           |



***REST is principle and RESTful is implementation of REST principle.***

## Q. What is Content Negotiation in Web API?
Content Negotiation is the process by which the server and the client agree on the format (media type) of the data that will be sent in the HTTP response.

In simple terms:

***It’s how a Web API decides whether to return data in JSON, XML, HTML, or another format — based on what the client requests.***

**Example**

If a client sends this HTTP request:
```
GET /api/students

Accept: application/json
```

The API will return:
```
[
  { "id": 1, "name": "Alice" },
  { "id": 2, "name": "Bob" }
]
```

But if another client sends:
```
GET /api/students
Accept: application/xml
````

Then the API responds:
```
<ArrayOfStudent>
  <Student>
    <Id>1</Id>
    <Name>Alice</Name>
  </Student>
  <Student>
    <Id>2</Id>
    <Name>Bob</Name>
  </Student>
</ArrayOfStudent>
```

**Same data, different representation.**
That’s content negotiation at work.

**How Content Negotiation Works (Step-by-Step)**
1. Client sends an HTTP request with an Accept header, e.g.:
```
Accept: application/json
```
2. Server checks available formatters (like JSON, XML).
3. Server chooses the best match based on what the client requested.
4. Response is sent in that format with the appropriate Content-Type header, e.g.:

**In ASP.NET Web API**

ASP.NET Web API uses media type formatters to handle content negotiation:

**Default Formatters:**
- JsonMediaTypeFormatter → For JSON (using application/json)
- XmlMediaTypeFormatter → For XML (using application/xml)

**You can also add:**
- FormUrlEncodedMediaTypeFormatter
- Custom formatters (e.g., CSV, plain text, YAML)

## Q. 1. What is .NET Standard?
**1. .NET Standard**

.NET Standard is a formal specification of a set of APIs (Application Programming Interfaces) that are available across all .NET implementations.

In simple terms:

 >  .NET Standard = a common set of base APIs shared by all .NET platforms.

It ensures that code written for one .NET platform (like .NET Core) can be used on another (like .NET Framework or Xamarin) without modification.

**2. Why .NET Standard Was Introduced**

Before .NET Standard, there were different .NET implementations:

| Framework          | Purpose                          |
| ------------------ | -------------------------------- |
| **.NET Framework** | Windows desktop and web apps     |
| **.NET Core**      | Cross-platform, high performance |
| **Xamarin**        | Mobile apps (iOS, Android)       |
| **Unity**          | Game development                 |


Each of these had different API sets, which caused compatibility problems — libraries written for one often didn’t work on another.

.NET Standard solved this by defining a shared API surface across all platforms.