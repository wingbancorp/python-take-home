# Wing Python Take Home

Create a mock food-ordering API that a client can hit and
get a list of available menu items, submit an order, and receive an order receipt.

## The project should:

- Be built with [Python](https://www.python.org) & [FastAPI](https://fastapi.tiangolo.com)
- Contain at least two routers in different files (i.e. `menu.py` & `orders.py`), as-well-as multiple endpoints
- Use modern features & best practices (dependency injection, services, etc)
- Contain a git repo with working commits (treat this like an actual project)
- Be publically hosted on [Github](https://github.com)
- **Bonus** - Create test-suites for your routers using `pytest`, documentation can be found [here](https://fastapi.tiangolo.com/tutorial/testing/)
- **Bonus** - Dockerize the project & connect it to a PostgreSQL database; use the database to store & fetch available menu items

## Example Endpoints

`GET /menu`

#### Response

```json
{
    "items": [
        {
            "id": "781d66c4-87aa-469f-88df-1117c77fb576",
            "name": "Brooklyn Spaghetti",
            "genre": "ITALIAN",
            "price": 14.99
        },
        {
            "id": "b9024fb1-c3d9-4c5f-b447-0826e86988b4",
            "name": "Lamb Gyro",
            "genre": "GREEK",
            "price": 12.99
        },
        {
            "id": "f4f81a55-8f3d-4ae1-ae80-c81f51c0c49c",
            "name": "Cheeseburger",
            "genre": "AMERICAN",
            "price": 9.99
        }
    ]
}
```

<br>

---

<br>

`POST /order`

#### Request

```json
{
    "items": [
        {
            "id": "781d66c4-87aa-469f-88df-1117c77fb576",
            "quantity": 1
        },
        {
            "id": "b9024fb1-c3d9-4c5f-b447-0826e86988b4",
            "quantity": 2
        },
        {
            "id": "f4f81a55-8f3d-4ae1-ae80-c81f51c0c49c",
            "quantity": 3
        },
    ]
}
```

#### Response

```json
{
    "order_id": "c424989e-6760-45bd-bacd-dad9a4e9efd6",
    "status": "IN-PROGRESS",
    "total": 70.94
}
```

<br>

---

<br>

`GET /order/:id`

#### Response

```json
{
    "id": "c424989e-6760-45bd-bacd-dad9a4e9efd6",
    "status": "COMPLETE",
    "total": 70.94,
    "items": [
        {
            "id": "781d66c4-87aa-469f-88df-1117c77fb576",
            "price": 14.99,
            "quantity": 1
        },
        {
            "id": "b9024fb1-c3d9-4c5f-b447-0826e86988b4",
            "price": 12.99,
            "quantity": 2
        },
        {
            "id": "f4f81a55-8f3d-4ae1-ae80-c81f51c0c49c",
            "price": 9.99,
            "quantity": 3
        }
    ]
}
```
