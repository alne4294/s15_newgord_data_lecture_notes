# Data Engineering Notes, Spring 2015

## Lecture 1

#### Topics around data engineering:
* Social Networks
* Data Analytics - sampling (made possible my statistics), machine learning 
* Storage - NoSQL (document, graph, key-value stores, columnar)
* Data Collection and Cleaning (character encodings, etc.)
* Infoviz - D3, Tableau, Excel, R

Data Modeling is hard.

#### Data Lifecycle
Question (curation, triage, persistence) -> collection/generation -> clean up -> storage -> processing/analysis -> query+visualize+act -> (back to beginning)

#### HTTP request and response cycle
http:// <-> http request or response (networking protocol, GET/POST/PUT/DELETE) -> HTML

## Lecture 2

* Use class wiki page
* Get student development pack

#### Github Markdown

* Two types: Github flavored (GFM) and standard (SM)
* Can be used for: styling, word formatting, images, lists (ordered and unordered), links, horizontal lines, tables, code blocks
* Two spaces or two enters create new paragraph

Daring Fireball - markdown

#### HTTP request and response cycle cont'd

Browser <--> Web/App Server <--> Handler

1. Browser sends request with relevant parameters to Server  
  - ebay.com/Products/10 where ebay.com is the address of Server and Products/10 are relevant parameters.  
2. Wait for Handler response  
  - HTML, files, etc., eg. index.html  
3. Browser does what it can, but will make more requests as needed   
  - Eg. when encountering \<img>, \<script>, etc. in index.html.

#### REST: REpresentational State Transfer

[REST](http://en.wikipedia.org/wiki/Representational_state_transfer "Wiki Link") is an architecture for creating webservices which allow anything connected to the network to cummunicate via a common communications protocol (HTTP, etc.). 

URI - > Identifies the name of a resource representation.

Resources have methods similiar to or the same as HTTP: 
  * Create
  * Read
  * Update
  * Destroy

**REST Example:**
```
Resource: /users (all) or /users/id (specific)
Operations on /users:

GET    - Read           (Return current state)
POST   - Create {DATA}  (Create user with appropriate data)
PUT    - Update         (Update existing user)
DELETE - Destroy        (Delete user)
```

**Considerations when designing service:**  
 1. What database type?  
 2. How to handle new contact ids?  
 3. What inputs are acceptable?  
 4. How to format outputs?  
 5. How to implement error handling?

## Lecture 3

#### RESTFUL WEB SERVICES

REST - architectural style for web services by Roy Fielding at UC Irvine.  (alternative to SOAP).  

Example REST resources:
```
GET /api/1.0/users
GET /api/1.0/users/0
POST /api/1.0/users
PUT /api/1.0/users/0
DELETE /api/1.0/users/0
GET /api/1.0/search?q=tattersail
```

JSON format is king for RESTful services. HTML and XML are also typical formats.

Data sent over POST and PUT. POSTS can contain everything in the url.  Or in the body of the HTTP request.

Authentication data appears in HTTP headers if the request needs to be authenticated (Basic, OAuth).

###### Operations on two resources:

```
GET /api/1.0/posts/0/comments/1
POST /api/1.0/posts/0/comments
```
Or:

While performing an operation on one resource, you reference other resources (by id) in the data that is sent with the request.

###### Issues
* Security - how do you authenticate users?
* Identity - how are ids assigned to resources?
* Failure - how do we handle failure situations?
  * In the example today, we can use JSON.
  * Could have used HTTP Status Codes (404, 500, etc.)
  * Most services will use combination of both.
* Persistence - how are resources stored?
