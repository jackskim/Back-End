# Virtual Reality Funding Platform

##API Documentation

### Dummy Data

#### Test users with projects

```
Users: [
  {
    "id": 1,
    "username": "admin",
    "password": "password"
    "name": "Test 1",
    "about": "test account",
    "projects": [
      {
        "id": 1, 
        "projectName": "Test project 1",
        "projectType": "Tech",
        "description": "Small tech business test project 1",
        "fundingAmount": 5000.00,
        "user_id": 1, 
      },
      {
        "id": 2, 
        "projectName": "Test project 2",
        "projectType": "Social",
        "description": "Small social business test project 2",
        "fundingAmount": 7500.00,
        "user_id": 1,
      },
    ]
  },
  {
    "id": 2, 
    "username": "admin2",
    "password": "password2",
    "name": "Test 2",
    "about": "test account 2",
    "projects": [
      {
        "id": 3, 
        "projectName": "Test project 3",
        "projectType": "Tech",
        "description": "Small tech business test project 3",
        "fundingAmount": 10000.00,
        "user_id": 2,
      },
    ]
  }
]
```

# Auth Routes
| Table | Method |       Endpoint |                      Description |
| ----- | :----: | -------------: | -------------------------------: |
| users |  POST  | /auth/register |            Registers a new user. |
| users |  POST  | /auth/login    | Logs in already registered user. |

## Register

### Registers a new user.

_Method URL:_ `/auth/register`

_HTTP Method:_ **[POST]**

#### Request Body 
| Name       |  Type  | Required |     Description |
| ---------  | :----: | -------: | --------------: |
| `username` | String |      Yes | Must be unique. |
| `password` | String |      Yes |                 |
| `name`     | String |      Yes |                 |
| `about`    | Text   |      Yes |                 |

#### Examples

```
{
  "username": "vrproject",
  "password": "ilovemoney",
  "name": "John",
  "about": "Tech developer"
}

```

#### Response

##### 201 (Created)

> If you successfully register a user, the endpoint will return an HTTP response with a status code `201`.

##### 400 (Bad Request)

> If you are missing a username or password, the endpoint will return an HTTP response with a status code of `400`.

##### 500 (Internal Service Error)

> If there is a server or database error, the endpoint will return an HTTP response with a status code of `500`.

## Login

### Logs in an already registered user.

_Method URL:_ `/auth/login`

_HTTP Method:_ **[POST]**

#### Request Body

| Name       |  Type  | 
| ---------- | :----: | ---------------------------------------------------------:
| `username` | String |                           Must match username in database.
| `password` | String | Must match password to corresponding username in database.

#### Example

```
{
  "username": "vrproject",
  "password": "ilovemoney"
}
```

