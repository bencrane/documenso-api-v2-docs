# Document Fields

## Get document field

Returns a single field. If you want to retrieve all the fields for a document, use the "Get Document" endpoint.

**Endpoint:** `GET /document/field/{fieldId}`

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
  const result = await documenso.documents.fields.get({
    fieldId: 6077.81,
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
  },
  "documentId": null,
  "templateId": null
}
```

---

## Create document field

Create a single field for a document.

**Endpoint:** `POST /document/field/create`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentId` | number | Yes | |
| `field` | object | Yes | |

#### Field Object

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `height` | number (min: 1) | Yes | |
| `pageNumber` | number (min: 1) | Yes | |
| `pageX` | number (min: 0) | Yes | |
| `pageY` | number (min: 0) | Yes | |
| `recipientId` | number | Yes | |
| `width` | number (min: 1) | Yes | |
| `fieldMeta` | object | No | |
| `type` | string | No | Values: `SIGNATURE` |

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
  const result = await documenso.documents.fields.create({
    documentId: 8001.93,
    field: {
      type: "NAME",
      recipientId: 2564.68,
      pageNumber: 791.77,
      pageX: 7845.22,
      pageY: 6843.16,
      width: 3932.15,
      height: 8879.89,
    },
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
  },
  "documentId": null,
  "templateId": null
}
```

---

## Create document fields

Create multiple fields for a document.

**Endpoint:** `POST /document/field/create-many`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentId` | number | Yes | |
| `fields` | array of objects | Yes | |

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
  const result = await documenso.documents.fields.createMany({
    documentId: 6257.51,
    fields: [
      {
        type: "FREE_SIGNATURE",
        recipientId: 679.35,
        pageNumber: 5914.59,
        pageX: 7253.11,
        pageY: 8426.91,
        width: 8995.55,
        height: 9808.97,
      },
    ],
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "fields": [
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

## Update document field

Update a single field for a document.

**Endpoint:** `POST /document/field/update`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentId` | number | Yes | |
| `field` | object | Yes | |

#### Field Object

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `id` | number | Yes | |
| `fieldMeta` | object | No | |
| `height` | number (min: 1) | No | |
| `pageNumber` | number (min: 1) | No | |
| `pageX` | number (min: 0) | No | |
| `pageY` | number (min: 0) | No | |
| `type` | string | No | Values: `SIGNATURE` |
| `width` | number (min: 1) | No | |

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
  const result = await documenso.documents.fields.update({
    documentId: 5956.26,
    field: {
      type: "FREE_SIGNATURE",
      id: 6955.16,
    },
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
  },
  "documentId": null,
  "templateId": null
}
```

---

## Update document fields

Update multiple fields for a document.

**Endpoint:** `POST /document/field/update-many`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentId` | number | Yes | |
| `fields` | array of objects | Yes | |

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
  const result = await documenso.documents.fields.updateMany({
    documentId: 9317.43,
    fields: [],
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "fields": [
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

## Delete document field

**Endpoint:** `POST /document/field/delete`

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
  const result = await documenso.documents.fields.delete({
    fieldId: 4748.27,
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