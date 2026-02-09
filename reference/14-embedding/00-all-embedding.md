# Embedding

## Create embedding presign token

Creates a presign token for embedding operations with configurable expiration time

**Endpoint:** `POST /embedding/create-presign-token`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `expiresIn` | number (min: 0, max: 10080) | No | Default: 60 |
| `scope` | string | No | |

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
  const result = await documenso.embedding.embeddingPresignCreateEmbeddingPresignToken({});

  console.log(result);
}

run();
```

### Response Example (200)

```json
{
  "token": "string",
  "expiresAt": "string",
  "expiresIn": 1
}
```

---

## Verify embedding presign token

Verifies a presign token for embedding operations and returns the associated API token

**Endpoint:** `POST /embedding/verify-presign-token`

### Request Body (required)

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `token` | string (min: 1) | Yes | |
| `scope` | string | No | |

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
  const result = await documenso.embedding.embeddingPresignVerifyEmbeddingPresignToken({
    token: "<value>",
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