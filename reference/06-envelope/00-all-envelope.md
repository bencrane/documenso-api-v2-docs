# Envelope

## Find envelopes

Find envelopes based on search criteria

**Endpoint:** `GET /envelope`

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `query` | string | No | The search query |
| `page` | number (min: 1) | No | The pagination page number, starts at 1 |
| `perPage` | number (min: 1, max: 100) | No | The number of items per page |
| `type` | string | No | Filter envelopes by type. Values: `DOCUMENT`, `TEMPLATE` |
| `templateId` | number | No | Filter envelopes by the template ID used to create it |
| `source` | string | No | Filter envelopes by how it was created. Values: `DOCUMENT`, `TEMPLATE`, `TEMPLATE_DIRECT_LINK` |
| `status` | string | No | Filter envelopes by the current status. Values: `DRAFT`, `PENDING`, `COMPLETED`, `REJECTED` |
| `folderId` | string | No | Filter envelopes by folder ID |
| `orderByColumn` | string | No | Values: `createdAt` |
| `orderByDirection` | string | No | Sort direction. Values: `asc`, `desc`. Default: `desc` |

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
  const result = await documenso.envelope.envelopeFind({});

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "data": [
    {
      "internalVersion": 1,
      "type": "DOCUMENT",
      "status": "DRAFT",
      "source": "DOCUMENT",
      "visibility": "EVERYONE",
      "templateType": "PUBLIC",
      "id": "string",
      "secondaryId": "string",
      "externalId": null,
      "createdAt": "string",
      "updatedAt": "string",
      "completedAt": null,
      "deletedAt": null,
      "title": "string",
      "authOptions": {
        "globalAccessAuth": ["ACCOUNT"],
        "globalActionAuth": ["ACCOUNT"]
      },
      "formValues": null,
      "publicTitle": "string",
      "publicDescription": "string",
      "userId": 1,
      "teamId": 1,
      "folderId": null,
      "templateId": null,
      "user": {
        "id": 1,
        "name": "string",
        "email": "string"
      },
      "recipients": [],
      "team": {
        "id": 1,
        "url": "string"
      }
    }
  ],
  "count": 1,
  "currentPage": 1,
  "perPage": 1,
  "totalPages": 1
}
```

---

## Get envelope audit logs

Find audit logs based on a search criteria

**Endpoint:** `GET /envelope/{envelopeId}/audit-log`

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `envelopeId` | string | Yes | Envelope ID |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `page` | number (min: 1) | No | The pagination page number, starts at 1 |
| `perPage` | number (min: 1, max: 100) | No | The number of items per page |
| `orderByColumn` | string | No | Values: `createdAt` |
| `orderByDirection` | string | No | Values: `asc`, `desc` |

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
  const result = await documenso.envelope.envelopeAuditLogFind({
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
      "createdAt": "string",
      "envelopeId": "string",
      "name": null,
      "email": null,
      "userId": null,
      "userAgent": null,
      "ipAddress": null,
      "type": "ENVELOPE_ITEM_CREATED",
      "data": {
        "envelopeItemId": "string",
        "envelopeItemTitle": "string"
      }
    }
  ],
  "count": 1,
  "currentPage": 1,
  "perPage": 1,
  "totalPages": 1
}
```

---

## Get envelope

Returns an envelope given an ID

**Endpoint:** `GET /envelope/{envelopeId}`

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `envelopeId` | string | Yes | |

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
  const result = await documenso.envelopes.get({
    envelopeId: "<id>",
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "internalVersion": 1,
  "type": "DOCUMENT",
  "status": "DRAFT",
  "source": "DOCUMENT",
  "visibility": "EVERYONE",
  "templateType": "PUBLIC",
  "id": "string",
  "secondaryId": "string",
  "externalId": null,
  "createdAt": "string",
  "updatedAt": "string",
  "completedAt": null,
  "deletedAt": null,
  "title": "string",
  "authOptions": {
    "globalAccessAuth": ["ACCOUNT"],
    "globalActionAuth": ["ACCOUNT"]
  },
  "formValues": null,
  "publicTitle": "string",
  "publicDescription": "string",
  "userId": 1,
  "teamId": 1,
  "folderId": null,
  "templateId": null,
  "documentMeta": {
    "signingOrder": "PARALLEL",
    "distributionMethod": "EMAIL",
    "id": "string",
    "subject": null,
    "message": null,
    "timezone": null,
    "dateFormat": null,
    "redirectUrl": null,
    "typedSignatureEnabled": true,
    "uploadSignatureEnabled": true,
    "drawSignatureEnabled": true,
    "allowDictateNextSigner": true,
    "language": "string",
    "emailSettings": {
      "recipientSigningRequest": true,
      "recipientRemoved": true,
      "recipientSigned": true,
      "documentPending": true,
      "documentCompleted": true,
      "documentDeleted": true,
      "ownerDocumentCompleted": true
    },
    "emailId": null,
    "emailReplyTo": null
  },
  "recipients": [
    {
      "envelopeId": "string",
      "role": "CC",
      "readStatus": "NOT_OPENED",
      "signingStatus": "NOT_SIGNED",
      "sendStatus": "NOT_SENT",
      "id": 1,
      "email": "string",
      "name": "string",
      "token": "string",
      "documentDeletedAt": null,
      "expired": null,
      "signedAt": null,
      "authOptions": {
        "accessAuth": ["ACCOUNT"],
        "actionAuth": ["ACCOUNT"]
      },
      "signingOrder": null,
      "rejectionReason": null
    }
  ],
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
      }
    }
  ],
  "envelopeItems": [
    {
      "envelopeId": "string",
      "id": "string",
      "title": "string",
      "order": 1
    }
  ],
  "directLink": {
    "directTemplateRecipientId": 1,
    "enabled": true,
    "id": "string",
    "token": "string"
  },
  "team": {
    "id": 1,
    "url": "string"
  },
  "user": {
    "id": 1,
    "name": "string",
    "email": "string"
  }
}
```

---

## Get multiple envelopes

Retrieve multiple envelopes by their IDs

**Endpoint:** `POST /envelope/get-many`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `ids` | object | Yes | Object with `type` (e.g., `envelopeId`) and `ids` array (1-20 items) |

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
  const result = await documenso.envelope.envelopeGetMany({
    ids: {
      type: "envelopeId",
      ids: [],
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
      "internalVersion": 1,
      "type": "DOCUMENT",
      "status": "DRAFT",
      "source": "DOCUMENT",
      "visibility": "EVERYONE",
      "templateType": "PUBLIC",
      "id": "string",
      "secondaryId": "string",
      "externalId": null,
      "createdAt": "string",
      "updatedAt": "string",
      "completedAt": null,
      "deletedAt": null,
      "title": "string",
      "authOptions": {
        "globalAccessAuth": ["ACCOUNT"],
        "globalActionAuth": ["ACCOUNT"]
      },
      "formValues": null,
      "publicTitle": "string",
      "publicDescription": "string",
      "userId": 1,
      "teamId": 1,
      "folderId": null,
      "templateId": null,
      "documentMeta": {},
      "recipients": [],
      "fields": [],
      "envelopeItems": [],
      "directLink": {},
      "team": {},
      "user": {}
    }
  ]
}
```

---

## Create envelope

Create an envelope using form data.

**Endpoint:** `POST /envelope/create`

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
  const result = await documenso.envelopes.create({
    payload: {
      title: "<value>",
      type: "TEMPLATE",
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

## Use envelope

Create a document envelope from a template envelope. Upload custom files to replace the template PDFs and map them to specific envelope items using identifiers.

**Endpoint:** `POST /envelope/use`

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
  const result = await documenso.envelopes.use({
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
  "id": "string",
  "recipients": [
    {
      "id": 1,
      "name": "string",
      "email": "string",
      "token": "string",
      "role": "CC",
      "signingOrder": null,
      "signingUrl": "string"
    }
  ]
}
```

---

## Update envelope

**Endpoint:** `POST /envelope/update`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `envelopeId` | string | Yes | |
| `data` | object | No | |
| `meta` | object | No | |

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
  const result = await documenso.envelopes.update({
    envelopeId: "<id>",
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "internalVersion": 1,
  "type": "DOCUMENT",
  "status": "DRAFT",
  "source": "DOCUMENT",
  "visibility": "EVERYONE",
  "templateType": "PUBLIC",
  "id": "string",
  "secondaryId": "string",
  "externalId": null,
  "createdAt": "string",
  "updatedAt": "string",
  "completedAt": null,
  "deletedAt": null,
  "title": "string",
  "authOptions": {
    "globalAccessAuth": ["ACCOUNT"],
    "globalActionAuth": ["ACCOUNT"]
  },
  "formValues": null,
  "publicTitle": "string",
  "publicDescription": "string",
  "userId": 1,
  "teamId": 1,
  "folderId": null
}
```

---

## Delete envelope

**Endpoint:** `POST /envelope/delete`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
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
  const result = await documenso.envelopes.delete({
    envelopeId: "<id>",
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

## Duplicate envelope

Duplicate an envelope with all its settings

**Endpoint:** `POST /envelope/duplicate`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
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
  const result = await documenso.envelopes.duplicate({
    envelopeId: "<id>",
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

## Distribute envelope

Send the envelope to recipients based on your distribution method

**Endpoint:** `POST /envelope/distribute`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `envelopeId` | string | Yes | |
| `meta` | object | No | |

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
  const result = await documenso.envelopes.distribute({
    envelopeId: "<id>",
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "success": true,
  "id": "string",
  "recipients": [
    {
      "id": 1,
      "name": "string",
      "email": "string",
      "token": "string",
      "role": "CC",
      "signingOrder": null,
      "signingUrl": "string"
    }
  ]
}
```

---

## Redistribute envelope

Redistribute the envelope to the provided recipients who have not actioned the envelope. Will use the distribution method set in the envelope

**Endpoint:** `POST /envelope/redistribute`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `envelopeId` | string | Yes | |
| `recipients` | array of numbers (min: 1) | Yes | |

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
  const result = await documenso.envelopes.redistribute({
    envelopeId: "<id>",
    recipients: [],
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "success": true,
  "id": "string",
  "recipients": [
    {
      "id": 1,
      "name": "string",
      "email": "string",
      "token": "string",
      "role": "CC",
      "signingOrder": null,
      "signingUrl": "string"
    }
  ]
}
```