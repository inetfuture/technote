HTTP is a implementation of REST.

## Verbs

Verb | Safe? | Idempotent? | Scenario |
-----| ---- | ---------- | -------- |
OPTIONS | Y | Y | get communication options(at least available verbs) |
GET | Y | Y | get resource |
HEAD | Y | Y | same with GET but no response body |
PUT | N | Y | create(if not exists)/relpace resource |
DELETE | N | Y | delete resource |
POST | N | N | create resource, unsafe operations there are no suitable verbs for |
PATCH | N | N | update resource partially |

## vs RPC style web service

RPC(SOAP):

- Use HTTP for tranfering enveloped data, only use POST verb.
- The key is method.
- Highweight.

RESTful:

- Stanard HTTP verbs for CRUD(POST, GET, PUT/PATCH, DELETE).
- The key is resource, resource-oriented.
- Lightweight, cross platform easily.

REST-RPC:

- No envelop, but also no standard HTTP verbs, represent method info in URI.

## Best Practice

- An API is a user interface for a developer - so put some effort into making it pleasant
- Use RESTful URLs and actions
- Use SSL everywhere, no exceptions
- An API is only as good as its documentation - so have great documentation
- Version via the URL, not via headers
- Use query parameters for advanced filtering, sorting & searching
- Provide a way to limit which fields are returned from the API
- Return something useful from POST, PATCH & PUT requests
- HATEOAS isn't practical just yet
- Use JSON where possible, XML only if you have to
- You should use camelCase with JSON, but snake_case is 20% easier to read
- Pretty print by default & ensure gzip is supported
- Don't use response envelopes by default
- Consider using JSON for POST, PUT and PATCH request bodies
- Paginate using Link headers
- Provide a way to autoload related resource representations
- Provide a way to override the HTTP method
- Provide useful response headers for rate limiting
- Use token based authentication, transported over OAuth2 where delegation is needed
- Include response headers that facilitate caching
- Define a consumable error payload
- Effectively use HTTP Status codes

## Examples

- http://developer.github.com/v3
