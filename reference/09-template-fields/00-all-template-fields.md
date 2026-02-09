# Template Fields

## Create template field

Create a single field for a template.

**Endpoint:** `POST /template/field/create`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `field` | object | Yes | |
| `templateId` | number | Yes | |

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
  const result = await documenso.templates.fields.create({
    templateId: 1203.71,
    field: {
      type: "DATE",
      recipientId: 2738.54,
      pageNumber: 5735.12,
      pageX: 2936.28,
      pageY: 8594.41,
      width: 7589.39,
      height: 3122.23,
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

## Get template field

Returns a single field. If you want to retrieve all the fields for a template, use the "Get Template" endpoint.

**Endpoint:** `GET /template/field/{fieldId}`

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
  const result = await documenso.templates.fields.get({
    fieldId: 1152.82,
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

## Create template fields

Create multiple fields for a template.

**Endpoint:** `POST /template/field/create-many`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `fields` | array of objects | Yes | |
| `templateId` | number | Yes | |

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
  const result = await documenso.templates.fields.createMany({
    templateId: 586.2,
    fields: [
      {
        type: "SIGNATURE",
        recipientId: 6990.12,
        pageNumber: 3472.45,
        pageX: 4747.87,
        pageY: 1673.94,
        width: 7215.37,
        height: 9417.43,
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

## Update template field

Update a single field for a template.

**Endpoint:** `POST /template/field/update`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `field` | object | Yes | |
| `templateId` | number | Yes | |

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
  const result = await documenso.templates.fields.update({
    templateId: 5083.07,
    field: {
      type: "TEXT",
      id: 1792.29,
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

## Update template fields

Update multiple fields for a template.

**Endpoint:** `POST /template/field/update-many`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `fields` | array of objects | Yes | |
| `templateId` | number | Yes | |

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
  const result = await documenso.templates.fields.updateMany({
    templateId: 3969.1,
    fields: [
      {
        type: "DROPDOWN",
        id: 2460.72,
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

## Delete template field

**Endpoint:** `POST /template/field/delete`

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
  const result = await documenso.templates.fields.delete({
    fieldId: 7996.49,
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