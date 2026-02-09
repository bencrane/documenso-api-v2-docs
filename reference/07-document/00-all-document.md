# Document

## Get document

Returns a document given an ID

**Endpoint:** `GET /document/{documentId}`

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `documentId` | number | Yes | |

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
  const result = await documenso.documents.get({
    documentId: 6150.61,
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "visibility": "EVERYONE",
  "status": "DRAFT",
  "source": "DOCUMENT",
  "id": 1,
  "externalId": null,
  "userId": 1,
  "authOptions": {
    "globalAccessAuth": ["ACCOUNT"],
    "globalActionAuth": ["ACCOUNT"]
  },
  "formValues": null,
  "title": "string",
  "createdAt": "string",
  "updatedAt": "string",
  "completedAt": null,
  "deletedAt": null,
  "teamId": 1,
  "folderId": null,
  "envelopeId": "string",
  "internalVersion": 1,
  "templateId": null,
  "documentDataId": "",
  "documentData": {
    "type": "S3_PATH",
    "id": "string",
    "data": "string",
    "initialData": "string",
    "envelopeItemId": "string"
  },
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
    "emailReplyTo": null,
    "password": null,
    "documentId": -1
  },
  "envelopeItems": [
    {
      "id": "string",
      "envelopeId": "string"
    }
  ],
  "folder": {
    "id": "string",
    "name": "string",
    "type": "DOCUMENT",
    "visibility": "EVERYONE",
    "userId": 1,
    "teamId": 1,
    "pinned": true,
    "parentId": null,
    "createdAt": "string",
    "updatedAt": "string"
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
      "rejectionReason": null,
      "documentId": null,
      "templateId": null
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
      },
      "documentId": null,
      "templateId": null
    }
  ]
}
```

---

## Get multiple documents

Retrieve multiple documents by their IDs

**Endpoint:** `POST /document/get-many`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentIds` | array of numbers (min: 1) | Yes | |

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
  const result = await documenso.document.documentGetMany({
    documentIds: [],
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
      "visibility": "EVERYONE",
      "status": "DRAFT",
      "source": "DOCUMENT",
      "id": 1,
      "externalId": null,
      "userId": 1,
      "authOptions": {
        "globalAccessAuth": ["ACCOUNT"],
        "globalActionAuth": ["ACCOUNT"]
      },
      "formValues": null,
      "title": "string",
      "createdAt": "string",
      "updatedAt": "string",
      "completedAt": null,
      "deletedAt": null,
      "teamId": 1,
      "folderId": null,
      "useLegacyFieldInsertion": true,
      "envelopeId": "string",
      "internalVersion": 1,
      "documentDataId": "",
      "templateId": null,
      "user": {
        "id": 1,
        "name": null,
        "email": "string"
      },
      "recipients": [],
      "team": {
        "id": 1,
        "url": "string"
      }
    }
  ]
}
```

---

## Find documents

Find documents based on a search criteria

**Endpoint:** `GET /document`

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `query` | string | No | The search query |
| `page` | number (min: 1) | No | The pagination page number, starts at 1 |
| `perPage` | number (min: 1, max: 100) | No | The number of items per page |
| `templateId` | number | No | Filter documents by the template ID used to create it |
| `source` | string | No | Filter documents by how it was created. Values: `DOCUMENT`, `TEMPLATE`, `TEMPLATE_DIRECT_LINK` |
| `status` | string | No | Filter documents by the current status. Values: `DRAFT`, `PENDING`, `COMPLETED`, `REJECTED` |
| `folderId` | string | No | Filter documents by folder ID |
| `orderByColumn` | string | No | Values: `createdAt` |
| `orderByDirection` | string | No | Values: `asc`, `desc`. Default: `desc` |

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
  const result = await documenso.documents.find({});

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "data": [
    {
      "visibility": "EVERYONE",
      "status": "DRAFT",
      "source": "DOCUMENT",
      "id": 1,
      "externalId": null,
      "userId": 1,
      "authOptions": {
        "globalAccessAuth": ["ACCOUNT"],
        "globalActionAuth": ["ACCOUNT"]
      },
      "formValues": null,
      "title": "string",
      "createdAt": "string",
      "updatedAt": "string",
      "completedAt": null,
      "deletedAt": null,
      "teamId": 1,
      "folderId": null,
      "useLegacyFieldInsertion": true,
      "envelopeId": "string",
      "internalVersion": 1,
      "documentDataId": "",
      "templateId": null,
      "user": {
        "id": 1,
        "name": null,
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

## Create document

Create a document using form data.

**Endpoint:** `POST /document/create`

**Content-Type:** `multipart/form-data`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `file` | string (binary) | Yes | |
| `payload` | object | Yes | |

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
import { openAsBlob } from "node:fs";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.documents.create({
    payload: {
      title: "<value>",
    },
    file: await openAsBlob("example.file"),
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "envelopeId": "string",
  "id": 1
}
```

---

## Update document

**Endpoint:** `POST /document/update`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentId` | number | Yes | |
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
  const result = await documenso.documents.update({
    documentId: 3428.95,
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "visibility": "EVERYONE",
  "status": "DRAFT",
  "source": "DOCUMENT",
  "id": 1,
  "externalId": null,
  "userId": 1,
  "authOptions": {
    "globalAccessAuth": ["ACCOUNT"],
    "globalActionAuth": ["ACCOUNT"]
  },
  "formValues": null,
  "title": "string",
  "createdAt": "string",
  "updatedAt": "string",
  "completedAt": null,
  "deletedAt": null,
  "teamId": 1,
  "folderId": null,
  "useLegacyFieldInsertion": true,
  "envelopeId": "string",
  "internalVersion": 1,
  "documentDataId": "",
  "templateId": null
}
```

---

## Delete document

**Endpoint:** `POST /document/delete`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentId` | number | Yes | |

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
  const result = await documenso.documents.delete({
    documentId: 3963.4,
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

## Duplicate document

**Endpoint:** `POST /document/duplicate`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentId` | number | Yes | |

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
  const result = await documenso.documents.duplicate({
    documentId: 5285.3,
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "id": "string",
  "documentId": 1
}
```

---

## Distribute document

Send the document out to recipients based on your distribution method

**Endpoint:** `POST /document/distribute`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentId` | number | Yes | |
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
  const result = await documenso.documents.distribute({
    documentId: 7548.74,
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "visibility": "EVERYONE",
  "status": "DRAFT",
  "source": "DOCUMENT",
  "id": 1,
  "externalId": null,
  "userId": 1,
  "authOptions": {
    "globalAccessAuth": ["ACCOUNT"],
    "globalActionAuth": ["ACCOUNT"]
  },
  "formValues": null,
  "title": "string",
  "createdAt": "string",
  "updatedAt": "string",
  "completedAt": null,
  "deletedAt": null,
  "teamId": 1,
  "folderId": null,
  "useLegacyFieldInsertion": true,
  "envelopeId": "string",
  "internalVersion": 1,
  "documentDataId": "",
  "templateId": null
}
```

---

## Redistribute document

Redistribute the document to the provided recipients who have not actioned the document. Will use the distribution method set in the document

**Endpoint:** `POST /document/redistribute`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentId` | number | Yes | |
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
  const result = await documenso.documents.redistribute({
    documentId: 9084.69,
    recipients: [6011.8, 4441.56, 4251.15],
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

## Download document

**Endpoint:** `GET /document/{documentId}/download`

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `documentId` | number | Yes | The ID of the document to download |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `version` | string | No | The version of the document to download. "signed" returns the completed document with signatures, "original" returns the original uploaded document. Values: `original`, `signed`. Default: `signed` |

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
  const result = await documenso.documents.download({
    documentId: 5396.97,
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
null
```

---

## Download document (beta)

Get a pre-signed download URL for the original or signed version of a document

**Endpoint:** `GET /document/{documentId}/download-beta`

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `documentId` | number | Yes | The ID of the document to download |

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `version` | string | No | The version of the document to download. "signed" returns the completed document with signatures, "original" returns the original uploaded document. Values: `original`, `signed`. Default: `signed` |

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
  const result = await documenso.document.documentDownload({
    documentId: 9550.11,
  });

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "downloadUrl": "string",
  "filename": "string",
  "contentType": "string"
}
```

---

## Create document (Beta - Deprecated)

You will need to upload the PDF to the provided URL returned. Note: Once V2 API is released, this will be removed since we will allow direct uploads, instead of using an upload URL.

**Endpoint:** `POST /document/create/beta`

> ⚠️ **Deprecated:** This endpoint is deprecated.

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `title` | string (min: 1, max: 255) | Yes | |
| `attachments` | array of objects | No | |
| `externalId` | string (max: 255) | No | |
| `folderId` | string | No | |
| `formValues` | object | No | |
| `globalAccessAuth` | array of strings | No | Values: `ACCOUNT`, `TWO_FACTOR_AUTH` |
| `globalActionAuth` | array of strings | No | Values: `ACCOUNT`, `PASSKEY`, `TWO_FACTOR_AUTH`, `PASSWORD` |
| `meta` | object | No | |
| `recipients` | array of objects | No | |
| `visibility` | string | No | Values: `EVERYONE`, `MANAGER_AND_ABOVE`, `ADMIN` |

### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

### Request Example (cURL)

```bash
curl https://app.documenso.com/api/v2/document/create/beta \
  --request POST \
  --header 'Content-Type: application/json' \
  --header 'Authorization: YOUR_SECRET_TOKEN' \
  --data '{
  "title": "",
  "externalId": "",
  "visibility": "EVERYONE",
  "globalAccessAuth": ["ACCOUNT"],
  "globalActionAuth": ["ACCOUNT"],
  "formValues": {
    "propertyName*": ""
  },
  "folderId": "",
  "recipients": [
    {
      "email": "",
      "name": "",
      "role": "CC",
      "signingOrder": 1,
      "accessAuth": [],
      "actionAuth": [],
      "fields": [
        {
          "type": "SIGNATURE",
          "fieldMeta": {
            "label": "",
            "placeholder": "",
            "required": true,
            "readOnly": true,
            "fontSize": 12,
            "type": "signature"
          }
        },
        {
          "pageNumber": 1,
          "pageX": 0,
          "pageY": 0,
          "width": 1,
          "height": 1
        }
      ]
    }
  ],
  "attachments": [
    {
      "label": "",
      "data": "",
      "type": "link"
    }
  ],
  "meta": {
    "subject": "",
    "message": "",
    "timezone": "",
    "dateFormat": "yyyy-MM-dd hh:mm a",
    "distributionMethod": "EMAIL",
    "signingOrder": "PARALLEL",
    "allowDictateNextSigner": true,
    "redirectUrl": "",
    "language": "de",
    "typedSignatureEnabled": true,
    "uploadSignatureEnabled": true,
    "drawSignatureEnabled": true,
    "emailId": null,
    "emailReplyTo": null,
    "emailSettings": {
      "recipientSigningRequest": true,
      "recipientRemoved": true,
      "recipientSigned": true,
      "documentPending": true,
      "documentCompleted": true,
      "documentDeleted": true,
      "ownerDocumentCompleted": true
    }
  }
}'
```

### Response Example (200)

```json
{
  "document": {
    "visibility": "EVERYONE",
    "status": "DRAFT",
    "source": "DOCUMENT",
    "id": 1,
    "externalId": null,
    "userId": 1,
    "authOptions": {
      "globalAccessAuth": ["ACCOUNT"],
      "globalActionAuth": ["ACCOUNT"]
    },
    "formValues": null,
    "title": "string",
    "createdAt": "string",
    "updatedAt": "string",
    "completedAt": null,
    "deletedAt": null,
    "teamId": 1,
    "folderId": null,
    "envelopeId": "string",
    "internalVersion": 1,
    "templateId": null,
    "documentDataId": "",
    "documentData": {},
    "documentMeta": {},
    "envelopeItems": [],
    "folder": {},
    "recipients": [],
    "fields": []
  },
  "uploadUrl": "string"
}
```

---

## Create attachment

Create a new attachment for a document

**Endpoint:** `POST /document/attachment/create`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `data` | object | Yes | |
| `documentId` | number | Yes | |

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
  const result = await documenso.documents.attachments.create({
    documentId: 7014.36,
    data: {
      label: "<value>",
      data: "https://cheerful-bourgeoisie.org/",
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

**Endpoint:** `POST /document/attachment/update`

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
  const result = await documenso.documents.attachments.update({
    id: "<id>",
    data: {
      label: "<value>",
      data: "https://tinted-ceramics.biz",
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

Delete an attachment from a document

**Endpoint:** `POST /document/attachment/delete`

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
  const result = await documenso.documents.attachments.delete({
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

---

## Find attachments

Find all attachments for a document

**Endpoint:** `GET /document/attachment`

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `documentId` | number | Yes | |

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
  const result = await documenso.documents.attachments.find({
    documentId: 965.17,
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