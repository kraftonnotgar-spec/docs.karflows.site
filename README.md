# KarFlows API Docs

This folder is a documentation starter for `docs.your-domain.com`.

It is designed for Mintlify first because Mintlify is fast to launch, clean for API products, and can read OpenAPI specs. The same `openapi/karflows.yaml` file can also be used later with Redocly, Scalar, Swagger UI, Speakeasy, Stainless, or OpenAPI Generator.

## Recommended Deployment

Use a documentation subdomain:

```text
docs.your-domain.com
```

Why a subdomain:

- Keeps docs separate from the SaaS application.
- Lets customers bookmark API references.
- Lets SDK generators and search engines point to a stable docs host.
- Makes it easier to add versioned docs later, for example `/v1`.

## Local Preview With Mintlify

Install Mintlify CLI globally or run it with `npx`:

```bash
npx mintlify dev
```

Run the command from this `docs` folder.

## Structure

```text
docs/
  mint.json
  introduction.mdx
  quickstart.mdx
  authentication.mdx
  openapi/karflows.yaml
  concepts/
  apis/
  sdks/
  reference/
```

## SDK Plan

After the OpenAPI file is stable, generate SDKs with one of these tools:

- Speakeasy: good for generated SDKs and docs automation.
- Stainless: polished SDKs, higher-end developer experience.
- OpenAPI Generator: open-source and flexible.

Recommended SDK order for KarFlows:

1. Node.js
2. PHP and Laravel
3. Python
4. cURL examples in every page
5. Go later when enterprise clients ask for it
