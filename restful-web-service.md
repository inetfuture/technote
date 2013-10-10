HTTP is a implementation of REST.

## Verbs

Verb | Safe? | Idempotent? | Scenario |
-----| ---- | ---------- | -------- |
GET | Y | Y | get resource |
POST | N | N | create resource, unsafe operations there are no suitable verbs for |
PATCH | N | N | update resource partially |
PUT | N | Y | create(if not exists)/relpace resource |
DELETE | N | Y | delete resource |

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