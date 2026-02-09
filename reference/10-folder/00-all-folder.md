# Folder

## Find folders

Find folders based on a search criteria

**Endpoint:** `GET /folder`

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `query` | string | No | The search query |
| `page` | number (min: 1) | No | The pagination page number, starts at 1 |
| `perPage` | number (min: 1, max: 100) | No | The number of items per page |
| `parentId` | string | No | |
| `type` | string | No | Values: `DOCUMENT`, `TEMPLATE` |

### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 404 | Not found |
| 500 | Internal server error |

### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.folders.find({});

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "data": [
    {
      "id": "string",
      "name": "string",
      "userId": 1,
      "teamId": 1,
      "parentId": null,
      "pinned": true,
      "createdAt": "string",
      "updatedAt": "string",
      "visibility": "EVERYONE",
      "type": "DOCUMENT"
    }
  ],
  "count": 1,
  "currentPage": 1,
  "perPage": 1,
  "totalPages": 1
}
```

---

## Create new folder

Creates a new folder in your team

**Endpoint:** `POST /folder/create`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | Yes | |
| `parentId` | string | No | |
| `type` | string | No | Values: `DOCUMENT`, `TEMPLATE` |

### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.folders.create({
    name: "<value>",
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "id": "string",
  "name": "string",
  "userId": 1,
  "teamId": 1,
  "parentId": null,
  "pinned": true,
  "createdAt": "string",
  "updatedAt": "string",
  "visibility": "EVERYONE",
  "type": "DOCUMENT"
}
```

---

## Update folder

Updates an existing folder

**Endpoint:** `POST /folder/update`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `data` | object | Yes | |
| `folderId` | string | Yes | |

### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.folders.update({
    folderId: "<id>",
    data: {},
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "id": "string",
  "name": "string",
  "userId": 1,
  "teamId": 1,
  "parentId": null,
  "pinned": true,
  "createdAt": "string",
  "updatedAt": "string",
  "visibility": "EVERYONE",
  "type": "DOCUMENT"
}
```

---

## Delete folder

Deletes an existing folder

**Endpoint:** `POST /folder/delete`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `folderId` | string | Yes | |

### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.folders.delete({
    folderId: "<id>",
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "success": true
}
```