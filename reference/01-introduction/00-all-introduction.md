# Documenso v2 API

**Version:** 1.0.0  
**OpenAPI:** 3.1.1

Welcome to the Documenso v2 API.

This API provides access to our system, which you can use to integrate applications, automate workflows, or build custom tools.

## Server

```
https://app.documenso.com/api/v2
```

## Authentication

All API requests require authentication via API key.

| Type | Name | Location |
|------|------|----------|
| apiKey | Authorization | Header |

### Example

```typescript
import { Documenso } from "@documenso/sdk-typescript";

const documenso = new Documenso({
  apiKey: process.env["DOCUMENSO_API_KEY"] ?? "",
});
```

## Client Libraries

- **TypeScript SDK:** `@documenso/sdk-typescript`