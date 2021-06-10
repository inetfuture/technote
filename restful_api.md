# RESTful API

> A RESTful API -- also referred to as a RESTful web service or REST API -- is based on representational state transfer (REST) technology, an architectural style and approach to communications often used in web services development.

## References

- https://martinfowler.com/articles/richardsonMaturityModel.html **[MUST READ]** :bangbang:
- [Web API Design: The Missing Link](https://cloud.google.com/apigee/resources/ebook/web-api-design-register/?int_source=website&int_medium=resources&int_campaign=ebook&int_content=web-api-design-ebook), you need to input your email to receive the ebook. **[MUST READ]** :bangbang:
- https://swagger.io/specification/v2/ **[MUST READ]** :bangbang:
- http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api
- http://github.com/interagent/http-api-design
- http://developer.github.com/v3

## Best Practices

Someone may be wondering what's the point of all this... Go away, I have nothing to say to you.

### Endpoint Design

- Keep in mind that REST is **resource oriented**, do not design endpoints without community well-known and consistent rules.
- Use **plural noun** in path for resource collection, like `/articles`, not `/article`.
- To represent a single resource of a collection, use path like `/articles/{id}`. The `{id}` is the unique identity(database id, unique name, etc) of a resource, and don't repeat the `{id}` in other request parameters.
- Use HTTP path and method combinations right, common CRUD(Create、Read、Update、Delete) cases are listed below:

    Resource Path | POST | GET | PUT | PATCH | DELETE
    -------- | ---- | --- | --- | ----- | ------
    `/articles` | create a new article | list articles | X | X | X
    `/articles/{id}` | X | get a article by id | update or create(if not exists yet) a article by id | update a article **partially** by id | delete a article by id

    Don't try to understand why, there is no why, just get used to them and remember them, and use this table as a cheat sheet when you're starting to practice.

- For unusual non-CRUD cases, if there is indeed no obvious resource abstraction you can think of, always use `POST` + verb-ended path, e.g.:
    - `POST /articles/{articleId}/translate`
    - `POST /articles/batchUpdate`
    - `POST /articles/batchDelete`

    Most of the time this is debatable, e.g., for an user login API, you can abstract the operation as creating a session, so `POST /users/{id}/sessions` can be used, but `POST /users/login` is also fine in this case. Just don't do `GET /users/login` or  `PUT /users`, etc, these obviously don't comply with above rules.

- Resources can be nested, e.g. `/articles/{articleId}/comments/{id}`, but not always necessary, `/comments/{id}` is also fine, this is more a matter of style.
- In some cases a property of a resource can be represented as a resource too, e.g. `PUT /articles/{id}/title`(but `PATCH /articles/{id}/title` is wrong, `title` is already an atomic resource, it can not be partially updated).
- Arbitrary meaningful information can be inserted into the resource path, e.g. `/it/articles`(site category route, meaning IT articles), `/articles/hot`(collection quick filter, only suitable for `GET`), even `/it/articles/hot`.
- A resource can be singleton without parent collection, e.g. `GET /appVersion`.
- DO NOT use `GET` for write or danger operation(user login etc), it's dangerous in Web security manner and semantically wrong.

### Access Control

- Don't trust client input, all id information should be extracted or derived from a signed access token that is generated on server side then issued to client(either by user login or administrator configuration), instead of being passed by client input.
- Don't only implement action or operation permissions and forget data or resource permissions, otherwise malicious user may have access to other users' data.

### Others

- Use HTTP response status code right(no need to repeat it in response body), avoid to create your own error codes unless absolutely necessary.
- Use Content-Type `application/json` for request/response body.
- To represent date and time in request or response, use string ISO 8601 or RFC 3339 standard format instead of Unix timestamp, it's more friendly for human, therefore more easier to debug. The same goes for enumeration fields, prefer strings over integers if possible.
- For error response design, please refer to [错误反馈设计](/README.md#错误反馈设计).
- As for versioning, pagination, filtering, sorting, batch operations, etc, there are no hard rules, but take some popular API as examples and **be consistent with yourself**.

## Misc

### RPC style web service vs RESTful API

RPC(SOAP, gRPC):

- Use HTTP/HTTP2 for transferring xml-based or binary enveloped data, only use POST method.
- Method-oriented.
- Heavyweight, usually requires client to use specify libraries and generate stub files before actually making any requests.
- High performance, more suitable for internal system communications, but not friendly for open API.

HTTP-RPC:

- No envelop, but also no conventional HTTP paths and methods, represent method info in path.

RESTful API:

- Standard HTTP methods for CRUD.
- Resource-oriented.
- Lightweight, cross platform easily, more friendly for open API.

### HTTP Methods

Method | Safe? | Idempotent? | Scenario |
-----| ---- | ---------- | -------- |
OPTIONS | Y | Y | get communication options(at least available methods) |
GET | Y | Y | get resource |
HEAD | Y | Y | same with GET but no response body |
PUT | N | Y | create(if not exists)/relpace resource |
DELETE | N | Y | delete resource |
POST | N | N | create resource, unsafe operations there are no suitable methods for |
PATCH | N | N | update resource partially |

### Parameter Types

- Path parameters, those passed through the URL path, usually are ids, like above.
- Query (string) parameters, those passed through the URL query string(the part behind ? character).
- Body parameters, those passed through the request body, usually in JSON format.

### URL Components

![URI_syntax_diagram.svg](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d6/URI_syntax_diagram.svg/1920px-URI_syntax_diagram.svg.png)
