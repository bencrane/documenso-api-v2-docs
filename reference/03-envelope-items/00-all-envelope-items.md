# Envelope Items

## Create envelope items

Create multiple envelope items for an envelope

**Endpoint:** `POST /envelope/item/create-many`

**Content-Type:** `multipart/form-data`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `payload` | object | Yes | |
| `files` | array of strings | No | |

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
  const result = await documenso.envelopes.items.createMany({
    payload: {
      envelopeId: "<id>",
    },
  });

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
      "title": "string",
      "envelopeId": "string",
      "order": 1
    }
  ]
}
```

---

## Update envelope items

Update multiple envelope items for an envelope

**Endpoint:** `POST /envelope/item/update-many`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `data` | array of objects (min: 1) | Yes | |
| `envelopeId` | string | Yes | |

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
  const result = await documenso.envelopes.items.updateMany({
    envelopeId: "<id>",
    data: [],
  });

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
      "order": 1,
      "title": "string",
      "envelopeId": "string"
    }
  ]
}
```

---

## Delete envelope item

Delete an envelope item from an envelope

**Endpoint:** `POST /envelope/item/delete`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `envelopeId` | string | Yes | |
| `envelopeItemId` | string | Yes | |

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
  const result = await documenso.envelopes.items.delete({
    envelopeId: "<id>",
    envelopeItemId: "<id>",
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

---

## Download an envelope item

Download an envelope item by its ID

**Endpoint:** `GET /envelope/item/{envelopeItemId}/download`

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `envelopeItemId` | string | Yes | The ID of the envelope item to download |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `version` | string | No | The version of the envelope item to download. "signed" returns the completed document with signatures, "original" returns the original uploaded document. Values: `original`, `signed`. Default: `signed` |

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
  const result = await documenso.envelopes.items.download({
    envelopeItemId: "<id>",
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
null
```