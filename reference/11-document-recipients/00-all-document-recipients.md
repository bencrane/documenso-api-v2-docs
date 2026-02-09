# Document Recipients

## Get document recipient

Returns a single recipient. If you want to retrieve all the recipients for a document, use the "Get Document" endpoint.

**Endpoint:** `GET /document/recipient/{recipientId}`

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `recipientId` | number | Yes | |

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
  const result = await documenso.documents.recipients.get({
    recipientId: 874.3,
  });

  console.log(result);
}

run();
```

### Response Example (200)

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

## Create document recipient

Create a single recipient for a document.

**Endpoint:** `POST /document/recipient/create`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentId` | number | Yes | |
| `recipient` | object | Yes | |

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
  const result = await documenso.documents.recipients.create({
    documentId: 3058.31,
    recipient: {
      email: "Ila.Steuber@yahoo.com",
      name: "<value>",
      role: "ASSISTANT",
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

## Create document recipients

Create multiple recipients for a document.

**Endpoint:** `POST /document/recipient/create-many`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentId` | number | Yes | |
| `recipients` | array of objects | Yes | |

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
  const result = await documenso.documents.recipients.createMany({
    documentId: 9983.95,
    recipients: [
      {
        email: "Roosevelt_Baumbach@yahoo.com",
        name: "<value>",
        role: "CC",
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

## Update document recipient

Update a single recipient for a document.

**Endpoint:** `POST /document/recipient/update`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentId` | number | Yes | |
| `recipient` | object | Yes | |

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
  const result = await documenso.documents.recipients.update({
    documentId: 7045.62,
    recipient: {
      id: 2224.05,
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

## Update document recipients

Update multiple recipients for a document.

**Endpoint:** `POST /document/recipient/update-many`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `documentId` | number | Yes | |
| `recipients` | array of objects | Yes | |

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
  const result = await documenso.documents.recipients.updateMany({
    documentId: 3189.76,
    recipients: [],
  });

  console.log(result);
}

run();
```

### Response Example (200)

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

## Delete document recipient

**Endpoint:** `POST /document/recipient/delete`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `recipientId` | number | Yes | |

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
  const result = await documenso.documents.recipients.delete({
    recipientId: 5490.43,
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