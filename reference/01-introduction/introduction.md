# Documenso v2 API

**Version:** v1.0.0  
**OpenAPI:** OAS 3.1.1

Welcome to the Documenso v2 API.

This API provides access to our system, which you can use to integrate applications, automate workflows, or build custom tools.

## Server

```
https://app.documenso.com/api/v2
```

## Authentication

- **Type:** apiKey
- **Name:** Authorization

---

## API Endpoints

### Envelope Attachments

| Method | Endpoint |
|--------|----------|
| GET | `/envelope/attachment` |
| POST | `/envelope/attachment/create` |
| POST | `/envelope/attachment/update` |
| POST | `/envelope/attachment/delete` |

### Envelope Items

| Method | Endpoint |
|--------|----------|
| POST | `/envelope/item/create-many` |
| POST | `/envelope/item/update-many` |
| POST | `/envelope/item/delete` |
| GET | `/envelope/item/{envelopeItemId}/download` |

### Envelope Recipients

| Method | Endpoint |
|--------|----------|
| GET | `/envelope/recipient/{recipientId}` |
| POST | `/envelope/recipient/create-many` |
| POST | `/envelope/recipient/update-many` |
| POST | `/envelope/recipient/delete` |

### Envelope Fields

| Method | Endpoint |
|--------|----------|
| GET | `/envelope/field/{fieldId}` |
| POST | `/envelope/field/create-many` |
| POST | `/envelope/field/update-many` |
| POST | `/envelope/field/delete` |

### Envelope

| Method | Endpoint |
|--------|----------|
| GET | `/envelope` |
| GET | `/envelope/{envelopeId}/audit-log` |
| GET | `/envelope/{envelopeId}` |
| POST | `/envelope/get-many` |
| POST | `/envelope/create` |
| POST | `/envelope/use` |
| POST | `/envelope/update` |
| POST | `/envelope/delete` |
| POST | `/envelope/duplicate` |
| POST | `/envelope/distribute` |
| POST | `/envelope/redistribute` |

### Document

| Method | Endpoint |
|--------|----------|
| GET | `/document/{documentId}` |
| POST | `/document/get-many` |
| GET | `/document` |
| POST | `/document/create` |
| POST | `/document/update` |
| POST | `/document/delete` |
| POST | `/document/duplicate` |
| POST | `/document/distribute` |
| POST | `/document/redistribute` |
| GET | `/document/{documentId}/download` |
| GET | `/document/{documentId}/download-beta` |
| POST | `/document/create/beta` |
| POST | `/document/attachment/create` |
| POST | `/document/attachment/update` |
| POST | `/document/attachment/delete` |
| GET | `/document/attachment` |

### Document Fields

| Method | Endpoint |
|--------|----------|
| GET | `/document/field/{fieldId}` |
| POST | `/document/field/create` |
| POST | `/document/field/create-many` |
| POST | `/document/field/update` |
| POST | `/document/field/update-many` |
| POST | `/document/field/delete` |

### Template Fields

| Method | Endpoint |
|--------|----------|
| POST | `/template/field/create` |
| GET | `/template/field/{fieldId}` |
| POST | `/template/field/create-many` |
| POST | `/template/field/update` |
| POST | `/template/field/update-many` |
| POST | `/template/field/delete` |

### Folder

| Method | Endpoint |
|--------|----------|
| GET | `/folder` |
| POST | `/folder/create` |
| POST | `/folder/update` |
| POST | `/folder/delete` |

### Document Recipients

| Method | Endpoint |
|--------|----------|
| GET | `/document/recipient/{recipientId}` |
| POST | `/document/recipient/create` |
| POST | `/document/recipient/create-many` |
| POST | `/document/recipient/update` |
| POST | `/document/recipient/update-many` |
| POST | `/document/recipient/delete` |

---

## Template Recipients

### Get template recipient

Returns a single recipient. If you want to retrieve all the recipients for a template, use the "Get Template" endpoint.

**Endpoint:** `GET /template/recipient/{recipientId}`

#### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `recipientId` | number | Yes | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 404 | Not found |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.recipients.get({
    recipientId: 9436.42,
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
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
  ],
  "documentId": null,
  "templateId": null
}
```

---

### Create template recipient

Create a single recipient for a template.

**Endpoint:** `POST /template/recipient/create`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `recipient` | object | Yes | |
| `templateId` | number | Yes | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.recipients.create({
    templateId: 5712.95,
    recipient: {
      email: "Gerhard88@yahoo.com",
      name: "<value>",
      role: "SIGNER",
    },
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
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
```

---

### Create template recipients

Create multiple recipients for a template.

**Endpoint:** `POST /template/recipient/create-many`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `recipients` | array of objects | Yes | |
| `templateId` | number | Yes | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.recipients.createMany({
    templateId: 5642.48,
    recipients: [],
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
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
  ]
}
```

---

### Update template recipient

Update a single recipient for a template.

**Endpoint:** `POST /template/recipient/update`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `recipient` | object | Yes | |
| `templateId` | number | Yes | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.recipients.update({
    templateId: 2984.61,
    recipient: {
      id: 8617.99,
    },
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
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
  ],
  "documentId": null,
  "templateId": null
}
```

---

### Update template recipients

Update multiple recipients for a template.

**Endpoint:** `POST /template/recipient/update-many`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `recipients` | array of objects | Yes | |
| `templateId` | number | Yes | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.recipients.updateMany({
    templateId: 5597.58,
    recipients: [
      {
        id: 1630.42,
      },
    ],
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
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
          "...": "[Additional Properties Truncated]"
        }
      ],
      "documentId": null,
      "templateId": null
    }
  ]
}
```

---

### Delete template recipient

**Endpoint:** `POST /template/recipient/delete`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `recipientId` | number | Yes | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.recipients.delete({
    recipientId: 312.69,
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "success": true
}
```

---

## Template

### Find templates

Find templates based on a search criteria

**Endpoint:** `GET /template`

#### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `query` | string | No | The search query |
| `page` | number (min: 1) | No | The pagination page number, starts at 1 |
| `perPage` | number (min: 1, max: 100) | No | The number of items per page |
| `type` | string | No | Filter templates by type. Values: `PUBLIC`, `PRIVATE` |
| `folderId` | string | No | The ID of the folder to filter templates by |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 404 | Not found |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.find({});

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "data": [
    {
      "type": "PUBLIC",
      "visibility": "EVERYONE",
      "id": 1,
      "externalId": null,
      "title": "string",
      "userId": 1,
      "teamId": 1,
      "authOptions": {
        "globalAccessAuth": ["ACCOUNT"],
        "globalActionAuth": ["ACCOUNT"]
      },
      "createdAt": "string",
      "updatedAt": "string",
      "publicTitle": "string",
      "publicDescription": "string",
      "folderId": null,
      "useLegacyFieldInsertion": true,
      "envelopeId": "string",
      "team": {
        "id": 1,
        "url": "string"
      },
      "fields": [],
      "recipients": [],
      "templateMeta": {
        "signingOrder": "PARALLEL",
        "distributionMethod": "EMAIL"
      },
      "directLink": {
        "token": "string",
        "enabled": true
      },
      "templateDocumentDataId": ""
    }
  ],
  "count": 1,
  "currentPage": 1,
  "perPage": 1,
  "totalPages": 1
}
```

---

### Get template

**Endpoint:** `GET /template/{templateId}`

#### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `templateId` | number | Yes | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 404 | Not found |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.get({
    templateId: 2128.54,
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "type": "PUBLIC",
  "visibility": "EVERYONE",
  "id": 1,
  "externalId": null,
  "title": "string",
  "userId": 1,
  "teamId": 1,
  "authOptions": {
    "globalAccessAuth": ["ACCOUNT"],
    "globalActionAuth": ["ACCOUNT"]
  },
  "createdAt": "string",
  "updatedAt": "string",
  "publicTitle": "string",
  "publicDescription": "string",
  "folderId": null,
  "envelopeId": "string",
  "templateDocumentDataId": "",
  "templateDocumentData": {
    "type": "S3_PATH",
    "id": "string",
    "data": "string",
    "initialData": "string",
    "envelopeItemId": "string"
  },
  "templateMeta": {
    "id": "string",
    "subject": null,
    "message": null,
    "timezone": null,
    "dateFormat": null,
    "signingOrder": "PARALLEL",
    "typedSignatureEnabled": true,
    "uploadSignatureEnabled": true,
    "drawSignatureEnabled": true,
    "allowDictateNextSigner": true,
    "distributionMethod": "EMAIL",
    "redirectUrl": null,
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
    "templateId": null
  },
  "directLink": {
    "id": "string",
    "envelopeId": "string",
    "token": "string",
    "createdAt": "string",
    "enabled": true,
    "directTemplateRecipientId": 1,
    "templateId": 1
  },
  "user": {
    "id": 1,
    "name": null,
    "email": "string"
  },
  "recipients": [],
  "fields": [],
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
  "envelopeItems": [
    {
      "id": "string",
      "envelopeId": "string"
    }
  ]
}
```

---

### Get multiple templates

Retrieve multiple templates by their IDs

**Endpoint:** `POST /template/get-many`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `templateIds` | array of numbers (min: 1 item) | Yes | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.template.templateGetMany({
    templateIds: [618.65, 1418.73, 1001.18],
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "data": [
    {
      "type": "PUBLIC",
      "visibility": "EVERYONE",
      "id": 1,
      "externalId": null,
      "title": "string",
      "userId": 1,
      "teamId": 1,
      "authOptions": {
        "globalAccessAuth": ["ACCOUNT"],
        "globalActionAuth": ["ACCOUNT"]
      },
      "createdAt": "string",
      "updatedAt": "string",
      "publicTitle": "string",
      "publicDescription": "string",
      "folderId": null,
      "useLegacyFieldInsertion": true,
      "envelopeId": "string",
      "team": {
        "id": 1,
        "url": "string"
      },
      "fields": [],
      "recipients": [],
      "templateMeta": {
        "signingOrder": "PARALLEL",
        "distributionMethod": "EMAIL"
      },
      "directLink": {
        "token": "string",
        "enabled": true
      },
      "templateDocumentDataId": ""
    }
  ]
}
```

---

### Create template

Create a new template

**Endpoint:** `POST /template/create`

**Content-Type:** `multipart/form-data`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `file` | string (binary) | Yes | |
| `payload` | object | Yes | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";
import { openAsBlob } from "node:fs";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.create({
    payload: {
      title: "<value>",
    },
    file: await openAsBlob("example.file"),
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "envelopeId": "string",
  "id": 1
}
```

---

### Create template (Beta)

You will need to upload the PDF to the provided URL returned. Note: Once V2 API is released, this will be removed since we will allow direct uploads, instead of using an upload URL.

**Endpoint:** `POST /template/create/beta`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `title` | string (min: 1, max: 255) | Yes | |
| `attachments` | array of objects | No | |
| `externalId` | string \| null | No | |
| `folderId` | string | No | |
| `globalAccessAuth` | array of strings | No | Values: `ACCOUNT`, `TWO_FACTOR_AUTH`. Default: `[]` |
| `globalActionAuth` | array of strings | No | Values: `ACCOUNT`, `PASSKEY`, `TWO_FACTOR_AUTH`, `PASSWORD`. Default: `[]` |
| `meta` | object | No | |
| `publicDescription` | string (min: 1, max: 256) | No | |
| `publicTitle` | string (min: 1, max: 50) | No | |
| `type` | string | No | Values: `PUBLIC`, `PRIVATE` |
| `visibility` | string | No | Values: `EVERYONE`, `MANAGER_AND_ABOVE`, `ADMIN` |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.template.templateCreateTemplateTemporary({
    title: "<value>",
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "template": {
    "type": "PUBLIC",
    "visibility": "EVERYONE",
    "id": 1,
    "externalId": null,
    "title": "string",
    "userId": 1,
    "teamId": 1,
    "authOptions": {
      "globalAccessAuth": ["ACCOUNT"],
      "globalActionAuth": ["ACCOUNT"]
    },
    "createdAt": "string",
    "updatedAt": "string",
    "publicTitle": "string",
    "publicDescription": "string",
    "folderId": null,
    "envelopeId": "string",
    "templateDocumentDataId": "",
    "templateDocumentData": {},
    "templateMeta": {},
    "directLink": {},
    "user": {},
    "recipients": [],
    "fields": [],
    "folder": {},
    "envelopeItems": []
  },
  "uploadUrl": "string"
}
```

---

### Update template

**Endpoint:** `POST /template/update`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `templateId` | number | Yes | |
| `data` | object | No | |
| `meta` | object | No | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.update({
    templateId: 9404.77,
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "type": "PUBLIC",
  "visibility": "EVERYONE",
  "id": 1,
  "externalId": null,
  "title": "string",
  "userId": 1,
  "teamId": 1,
  "authOptions": {
    "globalAccessAuth": ["ACCOUNT"],
    "globalActionAuth": ["ACCOUNT"]
  },
  "createdAt": "string",
  "updatedAt": "string",
  "publicTitle": "string",
  "publicDescription": "string",
  "folderId": null,
  "useLegacyFieldInsertion": true,
  "envelopeId": "string",
  "templateDocumentDataId": ""
}
```

---

### Duplicate template

**Endpoint:** `POST /template/duplicate`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `templateId` | number | Yes | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.duplicate({
    templateId: 2490.16,
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "type": "PUBLIC",
  "visibility": "EVERYONE",
  "id": 1,
  "externalId": null,
  "title": "string",
  "userId": 1,
  "teamId": 1,
  "authOptions": {
    "globalAccessAuth": ["ACCOUNT"],
    "globalActionAuth": ["ACCOUNT"]
  },
  "createdAt": "string",
  "updatedAt": "string",
  "publicTitle": "string",
  "publicDescription": "string",
  "folderId": null,
  "useLegacyFieldInsertion": true,
  "envelopeId": "string",
  "templateDocumentDataId": ""
}
```

---

### Delete template

**Endpoint:** `POST /template/delete`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `templateId` | number | Yes | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.delete({
    templateId: 536.89,
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "success": true
}
```

---

### Use template

Use the template to create a document

**Endpoint:** `POST /template/use`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `recipients` | array of objects | Yes | |
| `templateId` | number | Yes | |
| `attachments` | array of objects | No | |
| `customDocumentData` | array of objects | No | |
| `customDocumentDataId` | string | No | |
| `distributeDocument` | boolean | No | |
| `externalId` | string (max: 255) | No | |
| `folderId` | string | No | |
| `formValues` | object | No | |
| `override` | object | No | |
| `prefillFields` | array of objects | No | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.use({
    templateId: 7392.96,
    recipients: [],
  });

  console.log(result);
}

run();
```

#### Response Example (200)

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
  "documentData": {},
  "documentMeta": {},
  "envelopeItems": [],
  "folder": {},
  "recipients": [],
  "fields": []
}
```

---

### Create direct link

Create a direct link for a template

**Endpoint:** `POST /template/direct/create`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `templateId` | number | Yes | |
| `directRecipientId` | number | No | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.directLink.create({
    templateId: 5094.31,
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "id": "string",
  "token": "string",
  "createdAt": "string",
  "enabled": true,
  "directTemplateRecipientId": 1,
  "envelopeId": "string",
  "templateId": 1
}
```

---

### Delete direct link

Delete a direct link for a template

**Endpoint:** `POST /template/direct/delete`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `templateId` | number | Yes | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.directLink.delete({
    templateId: 9950.03,
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "success": true
}
```

---

### Toggle direct link

Enable or disable a direct link for a template

**Endpoint:** `POST /template/direct/toggle`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `enabled` | boolean | Yes | |
| `templateId` | number | Yes | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.templates.directLink.toggle({
    templateId: 6583.54,
    enabled: false,
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "id": "string",
  "token": "string",
  "createdAt": "string",
  "enabled": true,
  "directTemplateRecipientId": 1,
  "envelopeId": "string",
  "templateId": 1
}
```

---

## Embedding

### Create embedding presign token

Creates a presign token for embedding operations with configurable expiration time

**Endpoint:** `POST /embedding/create-presign-token`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `expiresIn` | number (min: 0, max: 10080) | No | Default: 60 |
| `scope` | string | No | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.embedding.embeddingPresignCreateEmbeddingPresignToken({});

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "token": "string",
  "expiresAt": "string",
  "expiresIn": 1
}
```

---

### Verify embedding presign token

Verifies a presign token for embedding operations and returns the associated API token

**Endpoint:** `POST /embedding/verify-presign-token`

#### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `token` | string (min: 1) | Yes | |
| `scope` | string | No | |

#### Responses

| Status | Description |
|--------|-------------|
| 200 | Successful response |
| 400 | Invalid input data |
| 401 | Authorization not provided |
| 403 | Insufficient access |
| 500 | Internal server error |

#### Request Example (TypeScript SDK)

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});

async function run() {
  const result = await documenso.embedding.embeddingPresignVerifyEmbeddingPresignToken({
    token: "<value>",
  });

  console.log(result);
}

run();
```

#### Response Example (200)

```json
{
  "success": true
}
```