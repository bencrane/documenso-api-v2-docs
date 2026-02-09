# Envelope Attachments

## Find attachments

Find all attachments for an envelope

**Endpoint:** `GET /envelope/attachment`

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `envelopeId` | string | Yes | |
| `token` | string | No | |

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
  const result = await documenso.envelopes.attachments.find({
    envelopeId: "<id>",
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
      "type": "link",
      "label": "string",
      "data": "string"
    }
  ]
}
```

---

## Create attachment

Create a new attachment for an envelope

**Endpoint:** `POST /envelope/attachment/create`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `data` | object | Yes | |
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
  const result = await documenso.envelopes.attachments.create({
    envelopeId: "<id>",
    data: {
      label: "<value>",
      data: "https://lustrous-skeleton.info",
    },
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "id": "string"
}
```

---

## Update attachment

Update an existing attachment

**Endpoint:** `POST /envelope/attachment/update`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `data` | object | Yes | |
| `id` | string | Yes | |

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
  const result = await documenso.envelopes.attachments.update({
    id: "<id>",
    data: {
      label: "<value>",
      data: "https://tough-premier.biz",
    },
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

## Delete attachment

Delete an attachment from an envelope

**Endpoint:** `POST /envelope/attachment/delete`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `id` | string | Yes | |

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
  const result = await documenso.envelopes.attachments.delete({
    id: "<id>",
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