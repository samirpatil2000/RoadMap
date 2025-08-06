# REST API Design Guide

This guide will help you design REST APIs for a network-based application, focusing on applying REST principles in the design process.

---

## 1. Identify the Resources (Object Modeling)

* **Resources** are the main objects in your application.
* Example resources:

  * `Devices`
  * `Configurations` (can be a sub-resource of Device)
  * `Web Assets`
  * `User Profiles`
* Each resource should have a unique identifier, e.g., `id`.

---

## 2. Create Resource URIs

* URIs should represent resources and their relationships.
* **Use nouns, not verbs, in URIs.**
* Use **hyphen-case** for readability in multi-word resource names.
* Example URIs:

  * `/devices`
  * `/devices/{id}`
  * `/configurations`
  * `/configurations/{id}`
  * `/devices/{id}/configurations`
  * `/devices/{id}/configurations/{configId}`
  * `/web-assets`
  * `/web-assets/{id}`
  * `/user-profiles`
  * `/user-profiles/{id}`

---

## 3. Determine Resource Representations

* Use simple formats like **JSON** or **XML** (JSON is recommended).
* **Collections** should return only essential info.
* **Single resources** should return complete info, including links to sub-resources.

### Example (in JSON):

**Device Collection:**

```json
{
  "devices": [
    {
      "id": 12345,
      "name": "apple-srx_200",
      "status": "active",
      "link": "/devices/12345"
    },
    {
      "id": 556677,
      "name": "apple-srx_200",
      "status": "active",
      "link": "/devices/556677"
    }
  ]
}
```

**Single Device:**

```json
{
  "id": 12345,
  "name": "apple-srx_100_lehar",
  "status": "active",
  "ipAddr": "192.168.21.9",
  "configurations": [
    { "id": 42342, "link": "/configurations/42342" },
    { "id": 675675, "link": "/configurations/675675" }
  ]
}
```

**Web Asset Collection:**

```json
{
  "web-assets": [
    {
      "id": "a1b2c3",
      "type": "image",
      "url": "https://cdn.example.com/assets/a1b2c3.png",
      "link": "/web-assets/a1b2c3"
    }
  ]
}
```

---

## 4. Assign HTTP Methods

Map CRUD operations to HTTP methods:

| Operation        | HTTP Method | URI Example                                  |
| ---------------- | ----------- | -------------------------------------------- |
| List all         | GET         | `/devices`, `/configurations`, `/web-assets` |
| Get one          | GET         | `/devices/{id}`, `/web-assets/{id}`          |
| List subresource | GET         | `/devices/{id}/configurations`               |
| Create           | POST        | `/devices`, `/configurations`, `/web-assets` |
| Update           | PUT         | `/devices/{id}`, `/web-assets/{id}`          |
| Delete           | DELETE      | `/devices/{id}`, `/web-assets/{id}`          |
| Apply config     | PUT         | `/devices/{id}/configurations`               |
| Remove config    | DELETE      | `/devices/{id}/configurations/{configId}`    |

* **POST**: Create (server assigns `id`).
* **PUT**: Update (idempotent).
* **DELETE**: Remove resource.
* For large collections, support pagination:

  * `/devices?startIndex=0&size=20`

---

## 5. Additional Notes

* URIs are always nouns.
* Use hyphen-case for multi-word resource names.
* Collections and single resources have different representations.
* Collections contain only essential info; single resources contain full details.
* Each resource/collection should have at least a self-link.
* Consider soft-deleting resources (add deleted_at field) instead of hard deletion.
* Think about other aspects like logging and service discovery.

---

**Happy Learning!**
