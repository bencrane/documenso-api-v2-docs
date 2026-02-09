# Template Recipients

## Get template recipient

Returns a single recipient. If you want to retrieve all the recipients for a template, use the "Get Template" endpoint.

**Endpoint:** `GET /template/recipient/{recipientId}`

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
  const result = await documenso.templates.recipients.get({
    recipientId: 9436.42,
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

## Create template recipient

Create a single recipient for a template.

**Endpoint:** `POST /template/recipient/create`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `recipient` | object | Yes | |
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

## Create template recipients

Create multiple recipients for a template.

**Endpoint:** `POST /template/recipient/create-many`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `recipients` | array of objects | Yes | |
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
  const result = await documenso.templates.recipients.createMany({
    templateId: 5642.48,
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
      "documentId": null,
      "templateId": null
    }
  ]
}
```

---

## Update template recipient

Update a single recipient for a template.

**Endpoint:** `POST /template/recipient/update`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `recipient` | object | Yes | |
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

## Update template recipients

Update multiple recipients for a template.

**Endpoint:** `POST /template/recipient/update-many`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `recipients` | array of objects | Yes | |
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

## Delete template recipient

**Endpoint:** `POST /template/recipient/delete`

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
  const result = await documenso.templates.recipients.delete({
    recipientId: 312.69,
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