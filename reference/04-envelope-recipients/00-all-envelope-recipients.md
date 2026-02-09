# Envelope Recipients

## Get envelope recipient

Returns an envelope recipient given an ID

**Endpoint:** `GET /envelope/recipient/{recipientId}`

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
  const result = await documenso.envelopes.recipients.get({
    recipientId: 8771.72,
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
  ]
}
```

---

## Create envelope recipients

Create multiple recipients for an envelope

**Endpoint:** `POST /envelope/recipient/create-many`

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
  const result = await documenso.envelopes.recipients.createMany({
    envelopeId: "<id>",
    data: [
      {
        email: "",
        name: "<value>",
        role: "SIGNER",
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
  "data": [
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
  ]
}
```

---

## Update envelope recipients

Update multiple recipients for an envelope

**Endpoint:** `POST /envelope/recipient/update-many`

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
  const result = await documenso.envelopes.recipients.updateMany({
    envelopeId: "<id>",
    data: [
      {
        id: 8894.57,
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
  "data": [
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

## Delete envelope recipient

Delete an envelope recipient

**Endpoint:** `POST /envelope/recipient/delete`

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
  const result = await documenso.envelopes.recipients.delete({
    recipientId: 4834.93,
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