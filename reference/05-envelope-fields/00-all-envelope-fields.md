# Envelope Fields

## Get envelope field

Returns an envelope field given an ID

**Endpoint:** `GET /envelope/field/{fieldId}`

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `fieldId` | number | Yes | |

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
  const result = await documenso.envelopes.fields.get({
    fieldId: 6981.76,
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "envelopeId": "string",
  "envelopeItemId": "string",
  "type": "SIGNATURE",
  "id": 1,
  "secondaryId": "string",
  "recipientId": 1,
  "page": 1,
  "positionX": null,
  "positionY": null,
  "width": null,
  "height": null,
  "customText": "string",
  "inserted": true,
  "fieldMeta": {
    "label": "string",
    "placeholder": "string",
    "required": true,
    "readOnly": true,
    "fontSize": 12,
    "type": "signature"
  }
}
```

---

## Create envelope fields

Create multiple fields for an envelope

**Endpoint:** `POST /envelope/field/create-many`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `data` | array of objects | Yes | |
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
  const result = await documenso.envelopes.fields.createMany({
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
      "envelopeId": "string",
      "envelopeItemId": "string",
      "type": "SIGNATURE",
      "id": 1,
      "secondaryId": "string",
      "recipientId": 1,
      "page": 1,
      "positionX": null,
      "positionY": null,
      "width": null,
      "height": null,
      "customText": "string",
      "inserted": true,
      "fieldMeta": {
        "label": "string",
        "placeholder": "string",
        "required": true,
        "readOnly": true,
        "fontSize": 12,
        "type": "signature"
      },
      "documentId": null,
      "templateId": null
    }
  ]
}
```

---

## Update envelope fields

Update multiple envelope fields for an envelope

**Endpoint:** `POST /envelope/field/update-many`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `data` | array of objects | Yes | |
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
  const result = await documenso.envelopes.fields.updateMany({
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
      "envelopeId": "string",
      "envelopeItemId": "string",
      "type": "SIGNATURE",
      "id": 1,
      "secondaryId": "string",
      "recipientId": 1,
      "page": 1,
      "positionX": null,
      "positionY": null,
      "width": null,
      "height": null,
      "customText": "string",
      "inserted": true,
      "fieldMeta": {
        "label": "string",
        "placeholder": "string",
        "required": true,
        "readOnly": true,
        "fontSize": 12,
        "type": "signature"
      },
      "documentId": null,
      "templateId": null
    }
  ]
}
```

---

## Delete envelope field

Delete an envelope field

**Endpoint:** `POST /envelope/field/delete`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `fieldId` | number | Yes | |

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
  const result = await documenso.envelopes.fields.delete({
    fieldId: 2481.37,
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