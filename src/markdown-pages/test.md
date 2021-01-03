---
title: "Portal API"
date: "2021-01-03"
---

## User

**GET** `/token-auth/`

## Dashboard

**GET** `/project_management/dashboard/`

## Compnay

**GET** `/project_management/companies/`

**GET** `/project_management/companies/:id`

## Project

**GET** `/project_management/projects/`

**GET** `/project_management/projects/:project_id/`

**DELETE** `/project_management/projects/:project_id/`

- response with 204

**PATCH** `/project_management/projects/:project_id`

- response: object

```
{
  "id": 0,
  "company": {
    "name": "string",
    "id": 0,
    "user": null
  },
  "users": [
    {
      "id": 0,
      "email": "string",
      "username": "string"
    }
  ],
  "assets": [
    {
      "id": 0,
      "name": "string",
      "location": "string",
      "asset_status": "string",
      "created_at": "string",
      "updated_at": "string",
      "lat": "52.372760",
      "lon": "4.893604"
    },
    ],
    "name": "string",
    "created_at": "string",
    "updated_at": "string",
    "location": "string",
    "lat": null,
    "lon": null,
    "project_type": "string"
}
```

### USERS

**GET** `/project_management/projects/:project_id/users/`

- response: object

```
{
  "count": 3,
  "next": null,
  "previous": null,
  "results": [
    {
      "id": 4,
      "username": "cristina",
      "last_login": "2020-12-15T09:57:19.585282Z",
      "date_joined": "2020-11-25T11:01:30Z",
      "email": "cristina@mavisoft.com"
    },
    {
      "id": 3,
      "username": "min",
      "last_login": "2020-12-17T19:40:51.370236Z",
      "date_joined": "2020-11-25T10:51:20Z",
      "email": "min@mavisoft.com"
    },
    {
      "id": 2,
      "username": "kieran",
      "last_login": "2020-12-18T21:12:55.263081Z",
      "date_joined": "2020-11-25T10:44:53Z",
      "email": ""
    }
  ]
}
```

**POST** `/project_management/projects/:project_id/users/`

- create a new user account
- body: object

```
{
    "username": "string",
    "email": "string"
}
```

- response: object

```
{
    "id": 6,
    "username": "test",
    "last_login": null,
    "date_joined": "2020-12-22T12:54:18.174579Z",
    "email": "test@mail.com"
}
```

**PATCH** `/project_management/projects/:project_id/users/:user_id/`

- add a existing user to the project
- response: object

```
{
  "id": 2,
  "username": "kieran",
  "last_login": "2020-12-18T21:12:55.263081Z",
  "date_joined": "2020-11-25T10:44:53Z",
  "email": ""
}
```

**DELETE** `/project_management/projects/:project_id/users/:user_id/?remove=true`

- remove user from the project
- response with 204

**DELETE** `/project_management/projects/:project_id/users/:user_id/`

- delete user account
- response with 204

## Asset

### ASSETS

**GET** `/project_management/assets/`

**POST** `/project_management/assets/`

- body: object

```
{
   "project_id": 0,
   "name": "string",
   "location": "string",
   "asset_status": "To Be Inspected",
   "lat": null,
   "lon": null
}
```

**GET** `/project_management/assets/:asset_id/`

**PATCH** `/project_management/assets/:asset_id/`

- body: object

```
{
   "project_id": 0,
   "name": "string",
   "location": "string",
   "asset_status": "To Be Inspected",
   "lat": "string",
   "lon": "string"
}
```

**DELETE** `/project_management/assets/:asset_id/`

### SPHERES

**GET** `/project_management/assets/:asset_id/spheres/`

**GET** `/project_management/assets/:asset_id/spheres/<pk>/`

### FOLDER

**GET** `/project_management/assets/:asset_id/folders/`

**GET** `/project_management/assets/:asset_id/folders/:folder_id/`

### DATA

**GET** `/project_management/assets/:asset_id/data/`

**GET** `/project_management/assets/:asset_id/data/:data_id/`

**GET** `/project_management/assets/:asset_id/data/<pk>/download/`

### DATA TAB

**GET** `/project_management/assets/:asset_id/data_tab/`

**GET** `/project_management/assets/:asset_id/data_tab/?folder_id=none&limit=5&offset=95`

### REPORTS

**GET** `/project_management/assets/:asset_id/reports/`

**GET** `/project_management/assets/:asset_id/reports/<pk>/`

**GET** `/project_management/assets/:asset_id/reports/<pk>/download/`

## Report

### REPORT LIST

**GET** `/project_management/reports/`

**POST** `/project_management/reports/`

### REPORT DETAILS

**GET** `/project_management/reports/:id/`

**PATCH** `/project_management/reports/:id/`

**DELETE** `/project_management/reports/:id/`

## Folder

**GET** `/project_management/folders/<pk>/`

## Data

**GET** `/project_management/data/:data_id/`

**GET** `/project_management/data/:data_id/download/`

## Reports

**GET** `/project_management/reports/`

**GET** `/project_management/reports/:report_id/`

**GET** `/project_management/reports/:report_id/download/`

## Spheres

**GET** `/project_management/spheres/<pk>/`

## Custom endpoints

> they only have one way of accessing them.
> They serve a specific functionality

**GET** `token-auth/`

**GET** `/project_management/dashboard/`

**GET** `<url>/download/`

**GET** `/project_management/assets/:asset_id/data_tab/`
